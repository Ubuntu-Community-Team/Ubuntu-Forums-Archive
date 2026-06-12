---
title: "I need a command"
date: 2008-12-03
forum: General Help
---

### Post by ali_williams on 2008-12-03
Hey all,

I have some files one is a master file with a list of names. Then I have 3 other files that have random names in them. I need a command to find out what names they have in common from the master file compared to the 3 random files. Here is an example of what I am talking about.

<master>
apple
frank
jackie

<random1>
balloon
jackie
sam

I need a command that will tell me that the names that are the same between the master file and random1 is jackie.

I tried the "comm" command but it doesnt seem to work you guys have any other ideas?

---

### Post by Titan8990 on 2008-12-03
Is this homework?

---

### Post by opscure on 2008-12-03
you can use a shell script to accomplish this.
first create a script.  call it something like filetest.sh in your home directory and put this in it:
```

#!/bin/sh
mkdir master
mkdir $1
cat master.txt |while read line; do touch master/${line}; done
cat $1.txt |while read line; do touch $1/${line}; done
diff -s -r master/ $1/ >diff.tmp
cat diff.tmp |grep File > diff.tmp
gedit diff.tmp
rm -rf master
rm -rf $1

```
Then call it through the command line like this:
```
sh filetest.sh random
```
where random is the beginning of the filename of the random.txt file... ie. leave out the .txt.

What this will do is create two directories one called master and one called random.  Then it will read each line and make a blank file with the line name.  Then it will do a recursive diff comparing both directories.  Finally it will grep out all the ones that don't match, open your matches in gedit, and remove the temporary directories.

I hard coded in the master.txt file.  If your file is called something other then this you will want to change that line.

---

### Post by ali_williams on 2008-12-03
> **Titan8990 said:**
> Is this homework?

It sounds like it but its not. I am working on a website where i pulled a list of users from the site from the database but they have 3 other tables that are used by 3 other programs that have user names as well. So we exported the usernames as a comma delimited file, and now we want to compare the usernames from the website to the 3 other databases they use for the forums, blog, and the free banner exchange they run. The reason for checking these files is because they want to merge databases and they need to see what usernames are in use.

---

### Post by mali2297 on 2008-12-03
If we may assume that there are not any duplicate names within the files, then this should work:
```

cat master.txt random1.txt | sort | uniq -d

```

---

### Post by opscure on 2008-12-03
> **mali2297 said:**
> If we may assume that there are not any duplicate names within the files, then this should work:
```

cat master.txt random1.txt | sort | uniq -d

```

There shouldn't be, he is working with usernames.
That's is much simpler.  nice.

---

### Post by sedawk on 2008-12-03
the "uniq" solution will work, when doing the comparison pairwise.

Another tool that comes to my mind is "join" (untested).

The old unix gurus created some tools to deal with simple
files in table format (today often known as *.csv files),
so join or one of its brothers might do the job too.

---

### Post by ali_williams on 2008-12-04
> **mali2297 said:**
> If we may assume that there are not any duplicate names within the files, then this should work:
```

cat master.txt random1.txt | sort | uniq -d

```

That did man thanks a lot!!!!

---

