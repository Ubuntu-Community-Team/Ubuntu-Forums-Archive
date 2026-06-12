---
title: "Possible to change &quot;Applications-Places-System&quot; menu?"
date: 2005-11-11
forum: Desktop Environments
---

### Post by Georgie-o on 2005-11-11
I know how to edit the content of this menu with the "Applications Menu Editor" but what I would like is to shorten or alter the actual titles "Applications-Places-System" on the panel.  Is this possible?

Thanks

---

### Post by AbtZ on 2008-01-03
Ahem. *bump*

Nobody? C'mon guys, it's been more than two years since he asked. I know it must be possible since different localized version have different names there...

---

### Post by remitaylor on 2008-02-05
*** bump ***

i've been looking for an answer to this for awhile now ... knowing gnome, i'm sure these strings are in an xml file somewhere, but i've never been able to find it ...

someone ... ?

please ... ?

---

### Post by Casual Fan on 2008-02-06
I've been looking into this and apparently it's not easy.

Try this:

Go to System>Help and Support

Click on Customising your Computer

Click on The Main Menu

Click on Customising the Panel Menubar

Click on System Administration Guide

That takes you to several sections of in-depth instructions on how to change menus. I haven't had a chance to learn it, but maybe someone with more time and interest can figure it out and share?

Hope this helps!

CF

---

### Post by AbtZ on 2008-02-06
I would much appreciate if you could copy+paste the instructions, as I seem to be unable to find them. There's no "Customizing your computer" link to click on when I open Help and Support.

It might be because I'm using Linux Mint, I don't know. :/

---

### Post by Casual Fan on 2008-02-06
[http://library.gnome.org/admin/system-admin-guide/stable/](http://library.gnome.org/admin/system-admin-guide/stable/)

Look in Section 2. :)

---

### Post by AbtZ on 2008-02-06
Thanks, bro.

Now to find the section that describes how to change the titles of the App/Places/System menu...

---

### Post by antrunner85 on 2008-03-22
HI, I am not really sure if you wanna do this, but so far its what I understood, correct me if  I am wrong. You want to change the   Applications-Places-System to one single menu, is that correct?

Well i was trying to do the same  and I found a really easy way that might work for you. 

1.-Right click on the panel bar --> Add to Panel --> Under utilities select **main menu**

After this you should have one single ubuntu icon that displays everything together.

After this you can just get rid of your last menu bar.

I hope this helps you.:)

---

### Post by AbtZ on 2008-03-22
If it only were that easy. I don't like the Gnome Main Menu -- it's too hierarchical, with too many levels to go through before you get to System->Preferences->Mouse, as an example.

We're looking for a way to change the text of the gnome panel so it will take up less space. Changing "Applications" into "Apps", for instance.

---

### Post by vphreeze on 2008-05-08
[QUOTE=antrunner85;4566804]1.-Right click on the panel bar --> Add to Panel --> Under utilities select **main menu**

After this you should have one single ubuntu icon that displays everything together...QUOTE]

this worked for me too, you end up with something similar to Windows, where you just have the Ubuntu logo and when you click that, "Applications - Places - System" is under that as a stacked menu instead of the 3 being side-by-side. the one that is one there by default is the "Menu Bar", but you want "**Main Menu**" instead.

---

### Post by qurgh on 2008-05-26
I figured out how to change the "Applications", "Places" and "System" titles in the gnome-panel. Basically you have to create a new translation file for those words and put it in en_US. If you aren't using the US local, you can add/change the gnome-panel-*.mo file to whatever you want it to be.

For en_US people here's the steps.

1) Make a new text file which has something like this in it:

```
msgid ""
msgstr ""
"Project-Id-Version: gnome-panel trunk\n"
"Report-Msgid-Bugs-To: \n"
"POT-Creation-Date: 2008-05-26 00:59+0000\n"
"PO-Revision-Date: 2008-05-26 00:59+0000\n"
"Last-Translator: YOUR NAMR\n"
"Language-Team: None\n"
"MIME-Version: 1.0\n"
"Content-Type: text/plain; charset=UTF-8\n"
"Content-Transfer-Encoding: 8bit\n"
"Plural-Forms: nplurals=1; plural=0;\n"
"X-Launchpad-Export-Date: 2008-04-16 01:47+0000\n"
"X-Generator: Launchpad (build Unknown)\n"

msgid "Applications"
msgstr "YOUR NAME FOR APPLICATIONS"

msgid "Places"
msgstr "YOUR NAME FOR PLACES"

msgid "System"
msgstr "YOUR NAME FOR SYSTEM"

```

2) In a terminal run "msgfmt THE-FILENAME-OF-THE-TEXT-FILE"

3) Then run "sudo mv messages.mo /usr/share/locale-langpack/en_US/LC_MESSAGES/gnome-panel-2.0.mo"

4) Then run "pkill gnome-panel" and it'll work.

Here's a screen shot to show some changes:

[IMG]http://www.wizage.net/Appschanged.png[/IMG]

Have fun.

---

### Post by peakpc on 2008-06-08
Any side effects?  Seems to good to be true!! but it works!!

using "Apps" "GoTo" "Sys" gives me more room one my one panel (minimalist)

---

### Post by peakpc on 2008-06-14
Man I just can't get over how well this works (I've been looking for this a very long time) I wish this thread were bumped up to a how to! great work QURGH got any other words of wisdom?:):):)

---

