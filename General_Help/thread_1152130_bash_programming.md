---
title: "bash programming"
date: 2009-05-07
forum: General Help
---

### Post by bumdeal2 on 2009-05-07
My lecturer bet me 20 euro that i couldnt do this, which techinically speaking hes right, i was wandering of anyone could help me out so i could rub it in his face!!!!!!!mwhahahah:-P
 
 
Write a Shell script to analyse the disk usage of students in a particular class.
The program should allow the user running the script to input the particular class name (group name) as an argument to the script.
The script should create a file called “logfile” in the home directory of the user running the script. The first line of logfile should contain the heading:
“List of members of class “classname” on “today’s time and date”
For each member of the class, the script should record in the logfile on separate lines:
The username
The total number of files in the student’s home directory
The total disk space used by the student
The last line of the logfile should contain the total number of students found in the class

---

### Post by kanikilu on 2009-05-07
From the Ubuntu forums Code of Conduct: > 6. While we are happy to serve as a resource for hints and for asking questions when you get stuck and need a little help, the Ubuntu Forums should not be thought of as a homework service. Please do not post your homework assignments expecting someone else to do it for you. Any such threads will be taken offline and warnings or infractions may be issued.

You didn't necessarily say this was "homework" verbatim, but it certainly smells like it ;) How about you try to solve the problem(s) yourself and come back with specific questions (detailing what you tried and where you got stuck).

---

### Post by tornadof3 on 2009-05-07
Surely this script would require root privileges to count files inside other users' home folders?

---

### Post by bumdeal2 on 2009-05-07
yep,

---

### Post by JK3mp on 2009-05-07
+1 to the above, though that was useless,bc (@tornadof3) he didn't state taht he would have to run it as normal users. I know its very possible and easily done with users on a single workstation, not entirely sure how to implement it into a network, and +1 again to the person who stated it was probably homework, cause it does seem fishy. And now i also ask, have you attempted it yourself? Homework or not, people like to see you made an effort at it first. Show us work you've tried, and things youve researched, actually DO some reading and look into shell scripting functions etc. THEN if you get stuck, we might help ;) ?

---

### Post by bumdeal2 on 2009-05-07
i assure u it is not homework i bet him that i could do anything he threw at me as a joke and before i knew it,it was 20quid and this little bugger.

---

### Post by prem1er on 2009-05-07
Homework or not. Show something and form a question and somebody will help.

---

### Post by bumdeal2 on 2009-05-07
trust me i have tried!!!!!!!for the past week i start writing the code and i keep on reaching stumbling blocks everywher and my head is at melting point, and its not for a network just a user:-(

---

### Post by prem1er on 2009-05-07
....post the code and show where you are stuck.

---

### Post by bumdeal2 on 2009-05-07
emm dont worry about the privilages they are set so we can read from the files. 

basically my code is this ,, now you have to remember that ive only been doing BASH for about 3  weeks  and no real knowledge of the system at all. My only strong point would be C programming but that seems to do nothing for me .

/etc/group. This file has a line for each group 
groupname:password:groupid:secondary members. 
The second file is /etc/passwd. This file has a line for each user username:x:userid:groupid:comments:home directory :default shell



code ive go so far.

#!/bin/bash
echo "Please Enter the glass group you want to display."
read choice

echo "you have selected to display group $choice as of `date` "

if [ f4 -d: /etc/passwd = $choice]
cat /etc/group | grep gname: | cut -d: -f4 | tr "," "\n"
ls -l | wc -l
du -h $USER
cat /etc/passwd | grep gname: | cut -d: -f4 | tr "," "\n" | wc -l
fi


Now yes you may call me a retard fine  but im genuinely stuck and have no clue what to do  since my only real base of computing is C.

If you can help its appreciated if not no worries.

---

### Post by shabazzk on 2009-05-16
Can't help you but, if this is a bet, I think the Prof is suckering you into doing work he needs done for himself. 

If you REALLY want to get him, show him a working example, if you achieve it, but don't give him the code, unless he pays double, maybe even triple.:popcorn:

---

