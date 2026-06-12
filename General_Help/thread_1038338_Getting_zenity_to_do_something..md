---
title: "Getting zenity to do something."
date: 2009-01-12
forum: General Help
---

### Post by frankstrudel on 2009-01-12
Hi

I'm trying to put in a shutdown dialog in crontab (after seeing [[COLOR="Lime"]this[/COLOR]]("http://martin.ankerl.com/2008/01/24/howto-get-enough-sleep-despite-stumbleupon-with-ubuntu/")) so that my computer will display a zenity question dialog and turn immediately if i click OK, turn off after i while if i do nothing and not turn off if i click cancel.

My current thoughts have been;
```

shutdown -h +5 
```

(then)
```

/usr/bin/zenity --display :0 --question --text="Are You Still Working?"
```

both of which i'm confident in, and have proven in terminal. My problem is how to get the yay/nay from zenity to cancel the shutdown. From reading [[COLOR="Lime"]this[/COLOR]]("http://my.opera.com/mysurface/blog/show.dml/501154"), I presume i need to use an if, and i need to use 'echo $?' as my argument. However, the following doesn't seem to do anything;

```
/usr/bin/zenity --display :0 --question --text="Are You Still Working?" if [ "echo $?" -eq "1" ] then shutdown -c else shutdown -h now sudo init 0; fi
```

What do I need to do to get it to function?

Many thanks

Frank

---

### Post by dcstar on 2009-01-14
> **frankstrudel said:**
> 
........
both of which i'm confident in, and have proven in terminal. My problem is how to get the yay/nay from zenity to cancel the shutdown. From reading [[COLOR="Lime"]this[/COLOR]]("http://my.opera.com/mysurface/blog/show.dml/501154"), I presume i need to use an if, and i need to use 'echo $?' as my argument. However, the following doesn't seem to do anything;

```
/usr/bin/zenity --display :0 --question --text="Are You Still Working?" if [ "echo $?" -eq "1" ] then shutdown -c else shutdown -h now sudo init 0; fi
```

What do I need to do to get it to function?


[http://linux.byexamples.com/archives/265/a-complete-zenity-dialog-examples-2/](http://linux.byexamples.com/archives/265/a-complete-zenity-dialog-examples-2/)

---

### Post by frankstrudel on 2009-01-14
That site is certainly useful in backing up what i thought about echo$? being what i need to get a number out of zenity; but my problem remains of how to take the 0 or 1 and get a command to act upon that; perhaps using an 'if'? Which is why, in my first post, I put 

```
if [ "echo $?" -eq "1" ] then shutdown -c else shutdown -h now sudo init 0; fi
```

on the end of my zenity dialog box command. But, as this just prevents the dialog box from showing, I presume I have either

a) Misunderstood how to format the if command 
or
b) Misunderstood how to embed the if command into the zenity command
or
c) Completely misunderstood how I should go about doing this

Any help?
Thanks
Frank

---

### Post by piratebill on 2009-01-14
I could be wrong (been a while since I did scripts in bash) but I thing the -eq is for strings.  Use an = for numerical values.

---

### Post by frankstrudel on 2009-01-20
> **piratebill said:**
> I could be wrong (been a while since I did scripts in bash) but I thing the -eq is for strings.  Use an = for numerical values.

Thank you, unfortunately I only get an error message (either way; -eq or = ) saying;

bash: syntax error near unexpected token `fi'

I suspect, therefore, that i've written the if command incorrectly?

Also, I'm reading around about bash after you mentioned it, and am wondering whether it would be better to put something like;

```
/usr/bin/zenity --display :0 --question --text="Are You Still Working?" && shutdown -c
```

Would this work as I imagine? i.e. when the zenity dialog returns a 1 instead of a 0, it won't do 'shutdown -c'?

I'll play around, but if anyone could point me in the right direction, I would be grateful.

---

### Post by frankstrudel on 2009-01-20
The following seems as if it would work to cancel the shutdown, completely avoiding the if command.

```
/usr/bin/zenity --display :0 --question --text="Prevent Shutdown?" && shutdown -c 
```

However, I would like to have the 'CANCEL' button in the dialog (outputting a 1) to immediately start shutting down the computer. I'm not sure how to do that without the if... any ideas?

Thanks

Frank

---

### Post by frankstrudel on 2009-01-21
I was hoping that

```
 /usr/bin/zenity --display :0 --question --text="Prevent Shutdown?" && shutdown -c || shutdown -h now 
``` 

would immediately shutdown the computer upon 'cancel', as in #6, but it seems to do both shutdown -c and shutdown -h now. I thought, from reading around, that || does the command after it if the command before it isn't done. Perhaps there's some sort of grammar/syntax I need to get it to recognise shutdown -c as the command before it.
I think the above command roughly means; 

Show dialog then cancel shutdown, otherwise shutdown now

what I want is

Show dialog, then cancel shutdown, otherwise shutdown now

How do I acheive that?

Or any suggestions as how better to have CANCEL to shutdown now?

Thanks,
Frank

---

