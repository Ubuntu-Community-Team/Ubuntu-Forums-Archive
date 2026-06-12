---
title: "Trouble accessing CLI - going insane!!!!!"
date: 2008-12-17
forum: General Help
---

### Post by Puffincx on 2008-12-17
Hi there,

I am trying to get into CLI so I can run the Nvidia installer to correct my graphics settings - I accidentally deleted my xorg file... I can't run the installer with xorg and desktop manager running.

Anyway, when I try to do this by typing:

sudo /etc/init.d/gdm stop

the system exits but hangs with a full black background and little cursor flashing in the top left corner...

I need to just perform a sh nvidia-linux-x86.run without xorg running... Any other ways to do this? I have tried recovery mode as a root user but I think ubunutu thinks I am an intruder so it gives my no permission.

Thanks.

---

### Post by Titan8990 on 2008-12-17
> I need to just perform a sh nvidia-linux-x86.run without xorg running... Any other ways to do this? I have tried recovery mode as a root user but I think ubunutu thinks I am an intruder so it gives my no permission.


The recovery mode root shell gives 100% full permissions.

Before trying to run that nvidia script try repairing your xorg.conf:


dpkg-reconfigure xserver-xorg

---

### Post by unutbu on 2008-12-17
Press ```
Ctrl-Alt-F2
```
This will bring up a virtual terminal.

Ctrl-Alt-F1 to Ctrl-Alt-F6 are all virtual terminals that you can acces any time you want. Ctrl-Alt-F7 is usually where gdm puts the first graphical X display.

---

### Post by starcannon on 2008-12-17
Heres a little guide I wrote, might wanna follow it note for note, don't worry be happy :)

This is a complete how to for installing the nvidia drivers; don't skip steps and it will walk you through the entire process(including getting into a CLI as opposed to a virtual terminal).
[http://ubuntuforums.org/showpost.php?p=5086971&postcount=6](http://ubuntuforums.org/showpost.php?p=5086971&postcount=6)

GL and have fun.

---

### Post by Puffincx on 2008-12-17
> **starcannon said:**
> Heres a little guide I wrote, might wanna follow it note for note, don't worry be happy :)

This is a complete how to for installing the nvidia drivers; don't skip steps and it will walk you through the entire process(including getting into a CLI as opposed to a virtual terminal).
[http://ubuntuforums.org/showpost.php?p=5086971&postcount=6](http://ubuntuforums.org/showpost.php?p=5086971&postcount=6)

GL and have fun.

lol that's the guide I am using - well that and the nvidia howto... hmm still no luck... I try pressing ctrl-alt-F1 as your guide says but nothing happens...

so I just skip to the next one to kill gde and the damn thing freezes...

---

### Post by Titan8990 on 2008-12-17
You could just ssh it and do your work...


sudo apt-get install ssh-server


Then from PuTTy or another Linux machine:


ssh <yourusername>@<youripaddress>

---

### Post by starcannon on 2008-12-17
> **Puffincx said:**
> lol that's the guide I am using - well that and the nvidia howto... hmm still no luck... I try pressing ctrl-alt-F1 as your guide says but nothing happens...

so I just skip to the next one to kill gde and the damn thing freezes...

Okay well lets see what we got here.
You have done all the instructions up to step 8 correct?

If so then at the login screen attempt CTRL+ALT+F1 or F2 or F3 or F4 or even F5

Of important note is that I am by nature a lazy person, trust me when I say that I did not write one single line in that guide that was not considered necessary, so skipping steps is not an option :) if a step did'nt work for you we have to find out why and solve the problem, simply skipping it won't work ;)

---

### Post by Puffincx on 2008-12-17
> **starcannon said:**
> Okay well lets see what we got here.
You have done all the instructions up to step 8 correct?

If so then at the login screen attempt CTRL+ALT+F1 or F2 or F3 or F4 or even F5

Of important note is that I am by nature a lazy person, trust me when I say that I did not write one single line in that guide that was not considered necessary, so skipping steps is not an option :) if a step did'nt work for you we have to find out why and solve the problem, simply skipping it won't work ;)

Am I meant to be in any particular program while pressing ctrl alt f1 - honeslty, it just does nothing. What is it meant to due, cause?

My f1,2,3,4 keys are all a bit funny... maybe I'll try another keyboard

---

### Post by Puffincx on 2008-12-17
hah how funny... my Microsoft keyboard appears to be &^&#^*... F keys were not working... Drivers all installed now though...

You know I did actually do this successfully the other week with the same keyboard.. I wonder what happened. 

its almost 2.30am here I have been up for hours...

Thanks again guys,

Oh, and I'm Stuart by the way :)

---

### Post by starcannon on 2008-12-17
The screen should go black after pressing CTRL+ALT+F1
in some cases the screen may not be centering on the monitor, to check if this is the case, while the screen is "black" blind typing:

[LIST=1]
[*]type your username and press enter
[*]type your password and press enter
[*]type the word "clear" with no quotes and press enter
[/LIST]
If screen centering is the issue, you will likely find that you have a portion of the terminal visible now. If not we'll continue trouble shooting why it is you can't get into the shell. If you like I'd be happy to ssh in and install the driver with/for you, takes me all of 5 minutes :) (i've done a few of these).

I'll keep hanging out and helping in anyway you desire.

---

### Post by starcannon on 2008-12-17
Congratulations Stuart!

Happy it wasn't me guide, sad it was your keyboard lol.

Dream of large penguins :)

---

### Post by Sukarn on 2008-12-17
> **starcannon said:**
> Dream of large penguins

What's that for?

---

### Post by starcannon on 2008-12-17
> **Sukarn said:**
> What's that for?
Lol me being goofy, and him being up till 2:30am working on his driver.

---

