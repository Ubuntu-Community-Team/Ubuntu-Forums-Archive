---
title: "Debian package generation and init-scripts"
date: 2008-12-04
forum: General Help
---

### Post by maddis on 2008-12-04
Hi,

There was bit old thread called: 'Howto make debian standard debs from scratch' that explained the basics how to make debian package. I got my package working, but there are still some things need to do that that thread doesn't cover.

One thing is init-scripts. I was able to generate the /etc/init.d script, but couldn't figure out what is the right way to do the symbolick links to runlevels so I use postinst to do them and postrm to remove them. Is there better/correct way?

Other was menu-items, but I think I just found something worth to try so only wide open item is those init-scripts.

*Okay, it seems that the menu-thing I was refering didn't work so I'll need help about that too.

---

### Post by gTinker on 2008-12-04
[QUOTE=maddis]
One thing is init-scripts. I was able to generate the /etc/init.d script, but couldn't figure out what is the right way to do the symbolick links to runlevels so I use postinst to do them and postrm to remove them. Is there better/correct way?[/quote]

You can create links with the ln command. If you type man ln in a terminal, the manual page for the ln command will display. It's pretty straightforward but ask if you need more help understanding what is in the manual.

[QUOTE=maddis]
Other was menu-items, but I think I just found something worth to try so only wide open item is those init-scripts.

*Okay, it seems that the menu-thing I was refering didn't work so I'll need help about that too.[/QUOTE]

Maybe it would be a good idea to tell us what you mean by "menu-thing" and "menu-items".

---

### Post by maddis on 2008-12-05
> **gTinker said:**
> You can create links with the ln command. If you type man ln in a terminal, the manual page for the ln command will display. It's pretty straightforward but ask if you need more help understanding what is in the manual.

Yes I know that and that is exactly I do now in the postinst script. I was just wondering if there is a built-in functionality for that since you can already automatically create the /etc/init.d script.

> 
Maybe it would be a good idea to tell us what you mean by "menu-thing" and "menu-items".
I must admit it was 'bit' vague description. What I want is that when I install my package it would automatically install itself to ubuntu menus like other X11 programs does. 

With 'menu-thingie' I ment that when I create template for the debian package there is menu.ex - file containing some sort of draft of how the menu item should be discribed. I renamed to menu  and modified to contain following:

```

?package(myprogram):needs="X11" section="Applications/Accessories"\
  title="MyProgram" command="myprogram"

```

When I installed the package that menu file got copied into /usr/share/menu under name myprogram, but that's it. Even if I run update-menus - command it won't appear in any menu and I canot find it in Applications -> Add/Remove - tool. 

So I'm guessing I'm missing something (something ubuntu related??), but I don't know what.

---

### Post by gTinker on 2008-12-05
[QUOTE=maddis]
One thing is init-scripts. I was able to generate the /etc/init.d script, but couldn't figure out what is the right way to do the symbolick links to runlevels so I use postinst to do them and postrm to remove them. Is there better/correct way?
[/QUOTE]

I think I misunderstood your question in my first post. Looking at it again, it seems you want to know how to add the symlinks for the script you put into /etc/init.d/ to the runlevels. But I might have misunderstood again.

maddis, that was covered in the link I gave you in an earlier post you made, when you were asking about shutdown.
[http://ubuntuforums.org/showthread.php?t=1000664](http://ubuntuforums.org/showthread.php?t=1000664)
You need to use update-rc.d with the appropriate number and runlevels you want to use.

I can't answer your menu question.

---

### Post by maddis on 2008-12-08
Thanks again. That update-rc.d is just what I need. I (again) somehow managed not to notice that at the first time even though I read through the thread that was mentioned in my first post.

---

