---
title: "SAS Append in Data step"
date: 2009-08-16
forum: Education &amp; Science
---

### Post by kjohansen on 2009-08-16
I dont know if there are any SAS people here but...

If I have something like the below which reads all files in a directory and makes a data set out of it. But each file has observations for the same ID for different time periods, so what I would like to do is read the first file and then append the second based on an ID or name field, then append the third and etc for several hundred files.

Is this possible?

```

data one;
length fil2read $40 lname $20 fname $20 state $2;
infile indata truncover;
input f2r $20.;
fil2read=’/dept/tsd/dataread/files/’||f2r;
infile dummy filevar=fil2read end=done;
do while(not done);
input lname : $20. fname : $20. state $ phone;
output;
end;
run;

```

FILE1:
A 1 2 3 4
B 5 6 7 8
C 8 9 1 1

FILE2: 
A 3 4 5 6
B 3 4 5 5

then many more files with the same format, hence why I dont want to manually create separate data sets and append them.

OUTPUT 
A 1 2 3 4 3 4 5 6
B 5 6 7 8 3 4 5 5 
C 8 9 1 1 . . . .

---

### Post by IanH on 2009-08-16
It would help to have a better idea how your data is structured (Does each file have the same number of observations for each id? If not, how do you want to handle this?). Also, it's been some time since I've had to deal with SAS, so my memory might be a little fuzzy. But, here goes:

To read the files, you'll need to use some macro commands. Something like this should work:
 %ls(datadirectory,csv);
 %let m=0;
 p, li { white-space: pre-wrap; }   %do %while("%scan(&files, %eval(&m+1), %str( ))" NE "");
         %let m=%eval(&m+1);
         %let file=%scan(&files, &m, %str( ));


        (PROC IMPORT stuff here. &file is the file to import, &m is a counter keeping track of how many files you've been through.)

        %end;

Once you have the files read in, you can either use merge and a macro loop to joing them (you'll probably need some more macro code to rename the variables), or transpose the data sets so you have one column/id, concatenate them, then transpose back into the desired format.

Hope that helps.

---

