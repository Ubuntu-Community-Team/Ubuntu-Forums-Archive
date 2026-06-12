---
title: "Themes not Installing"
date: 2009-03-26
forum: General Help
---

### Post by billytalent on 2009-03-26
Hey guys, 

for some reason no theme will install. Usually i go to system->preferences->appearance and just click and drag the theme in there but im getting error messages saying the themes are not valid. 

Anyone got any ideas?

---

### Post by jwh400 on 2009-03-26
Make sure it's a tar.gz file you're trying to install. If it's an rar, unpack that and the file you're after will likely be in that.

---

### Post by billytalent on 2009-03-26
> **jwh400 said:**
> Make sure it's a tar.gz file you're trying to install. If it's an rar, unpack that and the file you're after will likely be in that.

All files are .tar.gz everything like that is in order. 

I have looked everywhere, tracked my way back to see if i made any mistakes, but all looks well. 

Are limits to the amount of themes you can add maybe?

---

### Post by Therion on 2009-03-26
Can you post a link to the themes you're trying to install?  

Sometimes the authors pack themes in such a way as to need special handling when installing.

---

### Post by .Maleficus. on 2009-03-26
You could also try unpacking them to ~/.themes and see if they show up that way.

---

### Post by billytalent on 2009-03-26
> **Therion said:**
> Can you post a link to the themes you're trying to install?  

Sometimes the authors pack themes in such a way as to need special handling when installing.

Ive tried it with 20+ themes and followed all of the ways they stipulated....all a no go :(

---

### Post by billytalent on 2009-03-26
bump :)

---

### Post by billytalent on 2009-03-26
Bump again :(

---

### Post by billytalent on 2009-03-27
Can anyone help?

---

### Post by sam1948 on 2009-03-27
> **Therion said:**
> Can you post a link to the themes you're trying to install? 

?
or link to them

---

### Post by .Maleficus. on 2009-03-27
> **HackerNeil said:**
> Can anyone help?
Did you try extracting them to ~/.themes?

Will you post links to the themes you're trying to install?


You need to help us help you.

---

### Post by billytalent on 2009-03-28
> **.Maleficus. said:**
> Did you try extracting them to ~/.themes?

Will you post links to the themes you're trying to install?


You need to help us help you.

I never extract them although i have even tried that...i havent posted links to the themes because this is a problem across the board, no themes install. I tried it with 20+ themes. Im not a totaly linux noob :)

---

### Post by .Maleficus. on 2009-03-28
I'm going to sound like a broken record here, but why not try extracting them to ~/.themes?  Even if that doesn't fix the problem with the Appearance dialog, you could install a program like lxappearance and change them that way (and they will have to extracted to ~/.themes for lxappearance to find them).

Are you sure you have all of the correct GTK engines installed too?  Check that you have them all installed (search Synaptic for gtk-engine and you should get some results).

---

### Post by billytalent on 2009-03-28
> **.Maleficus. said:**
> I'm going to sound like a broken record here, but why not try extracting them to ~/.themes?  Even if that doesn't fix the problem with the Appearance dialog, you could install a program like lxappearance and change them that way (and they will have to extracted to ~/.themes for lxappearance to find them).

Are you sure you have all of the correct GTK engines installed too?  Check that you have them all installed (search Synaptic for gtk-engine and you should get some results).

I tried extracting theme to themes folder, was a no go...and i have all the gtk engines :(

---

### Post by billytalent on 2009-03-29
bump!

Tried all the things mentioned in this thread, any other stabs in the dark?

Do an os reinstall?

---

### Post by jwh400 on 2009-03-29
If you don't want to post a link can you at least tell us from what site you're getting the themes from? And possibly the name of one of the themes that won't install?

---

### Post by billytalent on 2009-03-30
> **jwh400 said:**
> If you don't want to post a link can you at least tell us from what site you're getting the themes from? And possibly the name of one of the themes that won't install?

I have tried 20+ themes from [this site]("http://www.gnome-look.org/"), and they all dont work!

---

### Post by oldos2er on 2009-03-30
Which version of Ubuntu are you running? Which themes are you trying to install, compiz? gtk 2.x? metacity?

---

### Post by Therion on 2009-03-30
We keep asking for a LINK to a particular theme you are trying to install for a REASON.

Different themes (Gtk, Icon, Compiz, et al.)* have different install methods.*

Different themes, depending on how the author packaged them, *have different install methods*.

I'm going to ask one more time for a link to ONE theme you are trying to install.  Just one.  Pick any theme you would like to see installed and post a link to it here in your thread.

---

### Post by billytalent on 2009-03-30
> **Therion said:**
> We keep asking for a LINK to a particular theme you are trying to install for a REASON.

Different themes (Gtk, Icon, Compiz, et al.)* have different install methods.*

Different themes, depending on how the author packaged them, *have different install methods*.

I'm going to ask one more time for a link to ONE theme you are trying to install.  Just one.  Pick any theme you would like to see installed and post a link to it here in your thread.

Sorry pal, here we go, this is one i was trying to install...its a gdm theme. 

[http://tinyurl.com/2gz6og](http://tinyurl.com/2gz6og)

---

### Post by billytalent on 2009-03-30
> **HackerNeil said:**
> Sorry pal, here we go, this is one i was trying to install...its a gdm theme. 

[http://tinyurl.com/2gz6og](http://tinyurl.com/2gz6og)

Im running 8.10 ubuntu btw

---

### Post by Therion on 2009-03-30
> **HackerNeil said:**
> Im running 8.10 ubuntu btw
Understand I'm really NOT trying to be a jerk about this, seriously, I'm trying to help.  

Okay, so you've got your new GDM and you understand that a GDM is not a full on system-wide "theme" right?  The only thing that's going to change when we install this bad-boy is the screen you see when you log in and use to enter your Username and Password, right?  I just want to be clear on this.

Okay... Now then, here's how you install a new GDM:

Put the the new GDM file you downloaded on your Desktop. 
Click on System/Administration/Login Window.
Click on "Local".
Click on "Add".
Navigate to the new GDM file on your Desktop.

Back at the top of the Login Window Preferences dialog box, use the drop-down menu that says "Theme" and choose the option for "Selected only".

You should see your new GMD in the list below.  
Click on it to select it.
Make sure it's the ONLY one selected in that list.
Click "Close".
Log out, and log back in.  
Your new GDM should show up.

Post back with problems, etc.

---

### Post by sam1948 on 2009-03-31
at last...
u were trying to install theme when the link u gave was 
theme for a login screen. those can be installed as it shown in the screen shots.
if u want a new theme for the complete windows icons and so on 
[_**[COLOR="Red"]start here[/COLOR]**_]("http://www.gnome-look.org/index.php?xsortmode=high&page=0&xcontentmode=150")

---

