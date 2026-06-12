---
title: "Empathy autostarts too early"
date: 2010-05-27
forum: Desktop Environments
---

### Post by x-shaney-x on 2010-05-27
I've added empathy to my startup applications because I tend to have it running all the time.
Problem is, roughly every 1 in 3 boots I get empathy in the system tray instead of the indicator.
Seems it's touch and go whether or not it starts up before the indicator applet.
I have tried renaming the startup entry to xx99-empathy to make sure it starts after everything else listed but it's not enough.

---

### Post by mike555 on 2010-05-28
to delay the startup of an app in the startup , use a command like ;
      
 by adding    bash -c "sleep 20:         to the command it sleeps for 20 seconds before starting . notice the spaces , and quotes (before sleep and after the command )  ....

     bash -c "sleep 20; /usr/bin/checkgmail"     for instance for checkgmail ......
   ==== put this Checkgmail text in the startup programs edit ====


  or ;

 putting   bash -c "sleep 20; /usr/bin/thunderbird"     in the startup list will start thunderbird 20 seconds after when you startup ... good to use with Thunderbirds add-on " firebird" , which can minimize Thunderbird to the top toolbar , letting it run and tell you when you have mail ...

---

### Post by x-shaney-x on 2010-05-28
Ahh, I did try sleep 5; empathy but it didn't start at all, must be because I needed the "bash".
I'll try that when I get back.

---

### Post by mike555 on 2010-05-29
you need to type it exactly , note the space and the quotes ...  I haven't tried it with empathy , but I think putting ;  [      bash -c "sleep 20; /usr/bin/empathy"   ]without the brackets ,in the startup list will start  empathy after 20 seconds .

---

### Post by x-shaney-x on 2010-05-29
Thanks, it's working perfectly.
Have the timeout at 5 at the moment which appears fine.  If I get the issue again I'll keep increasing til it starts properly everytime :)

---

### Post by mc1brew on 2011-09-01
I'm curious why the syntax has to be so specific in the "Startup Applications" program.  I would presume that the syntax could simply be the same as it would be in the terminal "sleep 5; empathy -h &".

Is there any reason it's so particular?

---

### Post by ascending_8 on 2011-09-14
> **mc1brew said:**
> I'm curious why the syntax has to be so specific in the "Startup Applications" program.  I would presume that the syntax could simply be the same as it would be in the terminal "sleep 5; empathy -h &".

Is there any reason it's so particular?

The problem is you are not running a bash session at startup.
bash is what  is running in a terminal and is required to interprets the commands.

---

