# utl-proc-import--option-nolabe--format-all-and-informat-all
proc import  option nolabe  format all and informat all
   %let pgm=utl-proc-import--option-nolabel--format-all-and-informat-all;

    option nolabel  format all informat all and proc import

    github
    https://tinyurl.com/n9sh4kte
    https://github.com/rogerjdeangelis/utl-proc-import--option-nolabe--format-all-and-informat-all

    SOAPBOX ON

        1, Making sure what you see is what is physicaly there
           Options nolabel; format _all_ and informata _all_ after set statements

           I use option 'NOLABEL' and format _all_; and informat _all_ ;after a
           Set statement to remove informats and formats. I do this because SAS defaults to
           To using the formats in many procedures and viewers. What you see may not be what you get.
           Any procs will default to using the label, and again what you see may not get.

        2. R create sas tables from R  csv with strings NA and Nan in numeric fields

           I often do not use 'proc import' to import csv files because when working with R and Python produced CSVs and other cases),
            guessing rows=max, will not work.
           This occurs when missing R numeric values are coded as strings NA and NaN,.

           CSV files created by R have multiple missing numeric types,
           'missing' R numerics can be NA or NaN(Not a Number). This is a real headache for programmers? Less is more.

           I DO use the proc import generated generated data step code.

           Also I read all variables as $char255 or longer when generated 'proc import code' shows longer strings.

           The array macro and my optimum length macro easily convert the appropriate numeric strings to numbers
           And reduce the size of string variables to max length observed.

           * Convert numeric strings to numbers.

           %array(nums,val=LD DA MOAI COMTI LD_COMTI);  * List of numeric variables, not automatic you need to know a little about your d

           Proc sql;
               Create
                  Table fixNum as
               select
                  %do_over(nums,Phrase=
                        Input(?,best32.) as ?,between=comma )
               ,*
               From
                  Imported_string_csv
           ;quit;
           The last ',*' variables that already exist will be ignored.

           %utl_optlen(inp=fixNum,out=fixNum);

           * these is also usefull

           %array(nums,%varlist(data=sashelp.class,keep=_numeric_));
           %array(nums,%varlist(data=sashelp.class,keep=_character_));


           I wonder why we communicate between languages and even within languages, when
           Base SAS and dropdown to R can inexpensively communicate using R dataframes, MySQL, Postgres..

    SOAPBOX OFF
