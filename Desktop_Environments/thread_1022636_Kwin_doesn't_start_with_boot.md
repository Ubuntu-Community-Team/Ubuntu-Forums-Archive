---
title: "Kwin doesn't start with boot"
date: 2008-12-27
forum: Desktop Environments
---

### Post by TiredBird on 2008-12-27
After each boot I have to manually start kwin in order to have a windows manager. I have to enter alt-f2 and 'kwin' after each boot. 

I installed this system about three days ago and it has worked fine up until tonight. 

I have compared my rcS.d and rc2.d directories with those of a working system. Both are Kubuntu 8.04 with kde 3.x. The most recent install, the one that is not working properly, has more scripts activated but eveyone that is active on the older system is activated on the new one.

Will someone please explain how I can fix this. I have searched the internet and this forum for an answer but can find none.

---

### Post by jpkotta on 2008-12-27
Do you mean kdm?  kdm is the program that you log in with.  kwin is the KDE window manager; it gets started after you log in.  Only kdm is started with init scripts (/etc/init.d/kdm).

---

### Post by rudihawk on 2008-12-27
Try add a command like:
```
kwin --replace
```

to your startup programs.

---

### Post by TiredBird on 2008-12-27
If I have my terminology correct, it is 'kwin' and not 'kdm' that is causing me the problem. 

I get a desktop which looks to be correct. Therefore I assume that the desktop manager, 'kdm', is loading okay. However, when I open a window, I get a window with no borders, one that can't be moved or resized. I assume this is because I have no window manager, that 'kwin' is not running, or at least not running properly. 

Further evidence to me of this is that I can call up a command window with 'alt-f2' and then enter 'kwin', after which everything works fine. Unfortunately, I have to do this after every boot, otherwise my windows don't look right and don't function right. 

I assume this to be a window manager problem, (kwin), and not a desktop manager problem, ('kdm'). Thank you for taking the time to read my post and offer your suggestions.

---

### Post by rudihawk on 2008-12-27
You are correct, kwin is the program that draws the borders and titlebars etc. 

KDM - is like a login GUI I think.(similiar to GDM) although I not sure what these do.  

Have you tried to add kwin to your startup programs? or did that not help?

---

### Post by TiredBird on 2008-12-27
> **rudihawk said:**
> You are correct, kwin is the program that draws the borders and titlebars etc. 

KDM - is like a login GUI I think.(similiar to GDM) although I not sure what these do.  

Have you tried to add kwin to your startup programs? or did that not help?

Actually, I'm still trying to figure out how to add a quote to my previous post, but I'll save that for later.

I have not yet added kwin to my startup programs. Where do you suggest I add it?

---

### Post by rudihawk on 2008-12-27
To add a quote - just click the "quote" button on the post you would like to quote :)

Well I would be able to tell you if I used KDE but I dumped it yesterday - went back to Gnome. 

Which version of KDE are you using? 4.1?

I think this might help:

Look for startup or something similiar in System Settings. 

then if you can find something like that add this as a new entry:
```
kwin --replace
``` - the "--replace " is just so that if there is another WM running (but not displaying for some reason) kwin will override it. 

Put any program or link you want in this folder:
```
~/.kde/Autostart/
```

EDIT: I found this: [Linky]("http://www.techrecipes.net/linux/automatically-run-program-on-kdes-startup.html") which may help you

Sorry that I can't be more helpful man :|

---

### Post by TiredBird on 2008-12-27
> **rudihawk said:**
> To add a quote - just click the "quote" button on the post you would like to quote :)

Well I would be able to tell you if I used KDE but I dumped it yesterday - went back to Gnome. 

Which version of KDE are you using? 4.1?

I think this might help:

Look for startup or something similiar in System Settings. 

then if you can find something like that add this as a new entry:
```
kwin --replace
``` - the "--replace " is just so that if there is another WM running (but not displaying for some reason) kwin will override it. 

Put any program or link you want in this folder:
```
~/.kde/Autostart/
```

EDIT: I found this: [Linky]("http://www.techrecipes.net/linux/automatically-run-program-on-kdes-startup.html") which may help you

Sorry that I can't be more helpful man :|

I haven't done as suggested above as I just received this. However, I did as follows:

I added the line 'kwin --replace' to my /etc/rc.local script. The message I got when it ran was 'kwin: cannot connect to x server [fail]'.

Then I changed it to just read 'kwin' as that is what I have been putting in as a command after booting in order to get it to work. Same message however.

In both cases, my desktop environment after the login was completed was sans the window manager.

I am using kde 3.x, whatever comes with the install disk.

I'll look at the link you suggested.

Thanks again.

---

### Post by TiredBird on 2008-12-27
> **rudihawk said:**
> 

EDIT: I found this: [Linky]("http://www.techrecipes.net/linux/automatically-run-program-on-kdes-startup.html") which may help you



I followed the link but only found the same thing about 'autostart' you had already mentioned.

---

### Post by TiredBird on 2008-12-27
Kwin fails at *login*, not at boot. 

I have done some experimentation by setting up a second user. Logging into the new user always works. However, logging into my original user *always fails*.

If I fix the failed user with the command 'kwin', it remains fixed throughout user changes, (that is switching users without closing the session), however, as soon as I log out it is gone. 

On the other hand, no matter how many user switches I make, the new one always works.

I am about to compare the hidden files in the two user directories, to see if I can find what is causing the problem. 

I expect that to be a daunting task as my original user has lots of 'dot' files as a result of the many configuration changes that have been done, whereas the new user only has a few. 

Any suggestions will be greatly appreciated.

---

### Post by rudihawk on 2008-12-27
Compare the files in the new and the old users .kde directories for starters.

---

### Post by jpkotta on 2008-12-27
You shouldn't start kwin from /etc/rc.local.  That runs things as root, and you have to tell it exactly which X server to use (it is almost always :0 BTW). 

Try adding ```
export KDEWM="kwin --replace"
``` to your ~/.bashrc and/or ~/.bash_profile.

---

### Post by TiredBird on 2008-12-27
Sorry about being unresponsive but I had to leave for a couple of hours. 

> **jpkotta said:**
> Try adding ```
export KDEWM="kwin --replace"
``` to your ~/.bashrc and/or ~/.bash_profile.

Right now I am set up to compare the directories. Before I left I added a third user. I performed some activities with each of the first two, including using the command 'kwin' on the first one, then logged out of both before leaving. 

Now I should be able to review time stamps for each directory to find out which files got changed by certain events. Hopefully that will allow me to find the difference.

Your suggestion looks like a good one and it will probably work, but it won't tell me what went wrong. I'm going to try to find that out first.

Thanks for your help and patience.

---

### Post by TiredBird on 2008-12-27
> **rudihawk said:**
> Compare the files in the new and the old users .kde directories for starters.

See the preceding post. I am going to do the comparison as I said and I suspect that it will lead me to differences in .kde as you have suggested. I'll let you know what I find. Thanks for the help.

---

### Post by diegoallen on 2009-01-04
in the kde menu go to system-->system preferences-->advanced tab
you should find an option for autostart there. Then add a new program for autostart, type ```
kwin --replace
``` Remember to complete the title and description in order to remember what you've done.

I have the spanish version of kubuntu, hope my translations are good.

---

### Post by michaeldadmum on 2009-02-03
I think this is a problem with compiz. Enable and disable the desktop effects solve this.

---

