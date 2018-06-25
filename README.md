# utl_how_to_select_exact_increments_with_sums_that_are_exact
How to select small exact increments with sums that are exact.  Keywords: sas sql join merge big data analytics macros oracle teradata mysql sas communities stackoverflow statistics artificial inteligence AI Python R Java Javascript WPS Matlab SPSS Scala Perl C C# Excel MS Access JSON graphics maps NLP natural language processing machine learning igraph DOSUBL DOW loop stackoverflow SAS community.

    How to select small exact increments with sums that are exact;

    Not too useful but might be good to know?

    Problem

      When I sum 10 million small increments

             0.000244140625

      I get the exact sum

             2441.4062500000

      However if I make a very small change in the increment (10-12)

             0.000244140624

      I get the incorrect sum

             2441.4062404565
                       xxxxx

    PEOCESS
    =======

    Data have;
      retain  sum 0;
      do rec=1 to 10000000;
         sum= sum+0.000244140625;
      end;
      output;
      put sum= 22.10;
    run;quit;



    SUM=2441.406250000000000

    But if I make even the smallest change

    Data have;

      retain  sum 0;
      do rec=1 to 10000000;
         sum= sum+0.000244140624;
      end;
      output;
      put sum= 22.10;
    run;quit;

    i don't get

    2441.406240000000000

    I get INCORRECT)

    SUM=2441.4062404565


    REASON
    =======

       0.000244140625  has an exact representation in IEEE floats.
       It is 2**(-12)

       Even a slight change in the last digit forces
       an approximation and thus the incorrect sum;

       %put %sysevalf(2**(-12));

        0.000244140625
