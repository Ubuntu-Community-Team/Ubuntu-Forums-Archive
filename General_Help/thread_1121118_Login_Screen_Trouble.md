---
title: "Login Screen Trouble"
date: 2009-04-09
forum: General Help
---

### Post by K_REY_C on 2009-04-09
Hi All,

I've been having trouble with logging in at the login screen. When I type the correct password the screen goes dark for a second and then comes right back to the same login screen... when I type it in wrong it tells me I have the wrong password and doesn't go dark. 

At this point I can't log in! 

Any help appreciated.

K_REY_C

---

### Post by Wayne_V on 2009-04-09
hit <ctrl>-<alt>-f1 and you should get a non GUI login.  Try logging in there.

<ctrl>-<alt>-f7 should take you back to the GUI login.

---

### Post by K_REY_C on 2009-04-09
I was able to login under the non-GUI interface but when I ctrl-alt-f7 I go back to the GUI login screen. 

Is there something I need to reset in the non-GUI terminal?

Thanks

---

### Post by Wayne_V on 2009-04-09
check the ~/.xsession-errors file to see if it has anything useful.

---

### Post by K_REY_C on 2009-04-09
How do I do that from the terminal?

Thanks!

---

### Post by connorh123 on 2009-04-09
This happens to me too, only it happens before. Then it goes into the login screen. It doesn't bother me that much.

---

### Post by Wayne_V on 2009-04-09
$ cat   ~/.xsession-errors

---

### Post by K_REY_C on 2009-04-09
This command isn't returning anything... it's like it registers as a command but simply returns to desktop:~$

Other thoughts?

Thanks!

---

### Post by K_REY_C on 2009-04-09
Anyone have any additional solutions to this problem? 

Any help appreciated. 

Thanks very much!

K_REY_C

---

### Post by Wayne_V on 2009-04-10
If you are able to log in at the console but not the gui the first thing I would suspect is a permissions problem.  From the console login:

$ cd
$ ls -ld ~
(make sure your home directory is owned by you)
$ ls -altr
(check  what files were changed most recently -- should see .xsession-errors)

You could try a clean gnome config:

$ mkdir SAVE
$ mv .gconf* .gnome* .config SAVE

And then try to log in to gnome again.

---

### Post by K_REY_C on 2009-04-11
[COLOR="Red"]My responses in red - more help needed![/COLOR]

> **Wayne_V said:**
> If you are able to log in at the console but not the gui the first thing I would suspect is a permissions problem.  From the console login:

$ cd
$ ls -ld ~
(make sure your home directory is owned by you)[COLOR="Red"]It is![/COLOR]
$ ls -altr
(check  what files were changed most recently -- should see .xsession-errors)[COLOR="Red"]See some errors... but don't know how to access them. It shows time/date and ".xsession-errors" but I'm not sure if that's some sort of byproduct from trying to fix earlier in the forum post.[/COLOR]

You could try a clean gnome config:

$ mkdir SAVE
[COLOR="Red"]says mkdir: cannot create directory 'save': no space left on device ... this shouldn't be true as I am certain the drive isn't full.[/COLOR]
$ mv .gconf* .gnome* .config SAVE
[COLOR="Red"]Should I go ahead and do this without being able to save? Last question: is there a way to reinstall the ubuntu OS from a live CD but leave the files? (I don't really understand how the OS works... but keep the ext2 and reinstall grub and swap? {correct me if I'm wrong on this assumption} Thank for all the help![/COLOR]
And then try to log in to gnome again.

---

### Post by Wayne_V on 2009-04-11
No - you need to address the space issue first.  That is likely what is causing the gui login to abort as well.

What does 'df -h' say?

---

### Post by K_REY_C on 2009-04-11
It's telling me that dev/sda1 is using 140gb of 147gb - 100%

So... the next question is how to rid myself of some data from the terminal, right? How do I go about doing that? Or, should I pop in a live cd and do it from there?

Thanks very much for all of your help!

K_REY_C

---

### Post by K_REY_C on 2009-04-12
A big huge thank you! Deleting the files did the trick. I had to learn how to use the terminal a little better (not a bad thing). I guess I had the kubuntu desktop and it took up enough space with its updates that I had forgotten to remove it after trying it out. 

Thanks again!

K_REY_C

---

