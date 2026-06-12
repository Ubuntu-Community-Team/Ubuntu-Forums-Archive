---
title: "no xml on kde"
date: 2006-02-15
forum: Desktop Environments
---

### Post by songo on 2006-02-15
hi..
i'm not able to see xml with konqueror.

eg, the result of the ballot.xml is:

XML parsing error
fatal parsing error: invalid name for processing instruction in line 45, column 6
<?xml version="1.0" encoding="ISO-8859-1"?>
         ^

ballot.xml
```

<?xml version="1.0" encoding="ISO-8859-1"?>
<!-- General ballot example -->

<ballot electionCode="1">
     <ballotDescription>
          <line>Example ballot</line>
          <line>Extra line</line>
          <!-- more lines -->
     </ballotDescription>
     <group code="1" description="Simple questions types"> 
          <!--type tag can have the values Single, Multiple, OpenS or OpenM-->     
          <question code="1" type="Single"> 
               <questionDescription>Is REVS robust?</questionDescription>
               <answer code="1">Yes</answer>
               <answer code="2">No</answer>
               <answer code="3">Don't know</answer>
          </question>
          <question code="2" type="Multiple"> 
               <questionDescription>Do you plan to use REVS in:</questionDescription>
               <answer code="1">National elections</answer>
               <answer code="2">Opinion surveys</answer>
               <answer code="3">Student elections</answer>
               <!-- more answers -->
          </question>
          <!-- more questions -->
     </group>
     <group code="2" description="Open questions types"> 
          <question code="1" type="OpenS"> 
               <questionDescription>What is your favorite color?</questionDescription>
               <answer code="1">Red</answer>
               <answer code="2">Green</answer>
               <answer code="3">Yellow</answer>
      <!-- more answers -->
          </question>
          <question code="2" type="OpenM"> 
               <questionDescription>What do you like to do in your free time?</questionDescription>
               <answer code="1">See a movie</answer>
               <answer code="2">Read a book</answer>
                    <!-- more answers -->
          </question>
          <!-- more questions -->
     </group>
     <!-- more groups -->
</ballot>

```

---

### Post by tagg3rx on 2006-02-15
Perhaps you should use firefox.....

Just a thought

I recomend automatix to install it and so much more
[http://ubuntuforums.org/showthread.php?t=66563](http://ubuntuforums.org/showthread.php?t=66563)

Automatix.... It just works

---

### Post by songo on 2006-02-15
i've tried to install firefox but i've failed! this is how new i am in linux. if you could help on that to, i appreciate.
anyway i can't use automatix that is just for brezzy. i have an hoary dist
tanx

---

### Post by tagg3rx on 2006-02-15
You just installed and your using Hoary.... intresting?

I'm pretty much a beginner my self and dont know the diffrences of hoary to breezy.

I would search symantec to see if opera or firefox is in there 
Or download the source files of firefox at there site and try to install it.

Here is a step by step guide to install FF 1.5
It looks intimidating but just take it one step at a time its quite detailed

[https://wiki.ubuntu.com/FirefoxNewVersion](https://wiki.ubuntu.com/FirefoxNewVersion)

hope this helps
if not maybe considering downloading breezy - unless your on dial up its not that big of a file.

---

### Post by songo on 2006-03-08
ok. i've installed firefox but the problem remains with the same message error! what should i do now? opera perhaps?

---

### Post by tagg3rx on 2006-03-08
I think your XML may have issues I'm no XML coder but i did the following to check the file.

I saved the text as test.xml on my windows xp box and tried to open it in both IE and firefox.  Both simply displayed the text.

I also did the same on ubuntu and viewed in firefox, konq, and opera
all 3 simply showed the text of the file.

---

### Post by AdrianVeidt on 2006-03-09
What you've got there is a bad xml file. Xml is extremely sensitive, compared to HTML. Xml will not let you get away with errors the way HTML will. Feedforall tells me that the file is "unreadable" and has "no root element". This file needs to be redesigned using a text editor before it will work.

---

### Post by songo on 2006-03-10
yeap...
the file had a error. i'm able now to open the correct files with firefox as tagg3rx sugested.
thanks

---

