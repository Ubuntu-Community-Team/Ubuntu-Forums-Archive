---
title: "shell script help?"
date: 2007-06-06
forum: Education &amp; Science
---

### Post by elfstone214 on 2007-06-06
hey guys, 

can someone help me do the following?

I need to read in the first and only line in myfile.txt which will be something like "case1" or "case2", etc. Then I need to create a directory with the name of that string which was read in (ie. a folder called case1).

I can read the line from the file using:
grep "case" myfile.txt

but I can't figure out how to use that and make the folder.

Thanks!

---

### Post by Stephen Howard on 2007-06-06
Sounds like a homework assignment!

---

### Post by Jergar on 2007-06-06
How about

name=`grep case file.txt`
mkdir $name

regards
Jergar

---

### Post by elfstone214 on 2007-06-06
> **Stephen Howard said:**
> Sounds like a homework assignment!

it's amazing how many times you can ask a question on this topic and get this answer ... it gets really old.

Anyway it is for part of one of my thesis codes. I need to randomize the folder which contains the input files because I will be using a quadcore processor and it may end up uploading muliple sets of input files (different cases) at the same time which will override the other.

---

### Post by elfstone214 on 2007-06-06
> **Jergar said:**
> How about

name=`grep case file.txt`
mkdir $name

regards
Jergar

Jergar,

thanks but I tried that you said and it created a directory called grep, and another called case

---

### Post by meatpan on 2007-06-06
> **elfstone214 said:**
> Jergar,

thanks but I tried that you said and it created a directory called grep, and another called case

It sounds like you used quotes instead of backticks. 

Quote:  '
backtick: `

The difference is subtle, which leads to some frustrating misunderstandings when reading or copying a script.  The backticks are instructions to the shell to run a command in a sub-shell.   The output of the sub-shell command is returned and can be assigned to a variable.  In this case, the variable name was assigned the output of : grep case file.txt

This type of backtick substitution is useful, and used fairly often in shell scripting.  Be aware that grep returns nothing if there is no match, and multiple values if there are multiple matches.  Because of that, consider:

```

name=`head -n 1 file.txt`
if [ -z $name ]; then
   mkdir $name
fi

```

This block of code will read the first line of the file, and then check whether or not name recieved an assignment.

---

### Post by bashologist on 2007-06-06
> **meatpan said:**
> It sounds like you used quotes instead of backticks. 
name=`head -n 1 file.txt`
if [ -z $name ]; then
   mkdir $name
fi


"-z" is zero length, "-n" is nonzero. I think you wanted "-n" here. Also, you forget to quote your variable in that test. And here's my solution to the backtick confusion:

```
man test
[http://wooledge.org/mywiki/BashFAQ#faq82](http://wooledge.org/mywiki/BashFAQ#faq82)
```

---

### Post by elfstone214 on 2007-06-06
thanks guys!

you were right I was using quote instead of backstick ... I have fallen for this more than once already #-o

---

### Post by mortenkjeldgaard on 2007-06-10
> you were right I was using quote instead of backstick ... I have fallen for this more than once already #-o

Yes backticks are a pain. Sometimes they are on dead keys. Fortunately, bash provides a special variable to do the same:

name=$(grep case text.txt)

I find that more readable than backticks.

Cheers,
Morten

---

