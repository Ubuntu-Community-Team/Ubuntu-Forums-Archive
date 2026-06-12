---
title: "Kate Text Editor...How Do I..."
date: 2009-05-26
forum: General Help
---

### Post by RVcook on 2009-05-26
I'm feeling so embarrassed to ask this but here goes...

In an attempt to get my Amarok 2 uninstalled (absolutely HATE that one) and reinstall Amarok 1.4, (which at least worked!) I followed some instructions that I found online and I must have entered something wrong.  Now I can't even get Synaptic Package Manager to load due to an error in the text editor.  **Ughh***](*,)*

My question:  How can I delete/remove the lines of text that were entered incorrectly?  These are the lines of text entered exactly as I was told.

[I]deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) jaunty-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) jaunty-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) jaunty-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) jaunty-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) jaunty-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) jaunty-security multiverse
deb [http://ppa.launchpad.net/bogdanb/ppa/ubuntu/jaunty](http://ppa.launchpad.net/bogdanb/ppa/ubuntu/jaunty) main[/I]

Notice there are no spaces or # signs...

And this is the error message I get:
[B][I]
The document could not be saved, as it was not possible to write to etc/apt/sources.list. Check that you have write access to this file or that enough disk space is available.[/I][/B]

I checked permissions and those are correct.  I checked disk space and I have plenty.

The REAL problem comes when I try to open Synaptic Pkg. Manager.  This is the error I get:

[I][B]An Error Occurred:  The following details are provided.

E: Malformed line 54 in source list /etc/apt/sources.list (dist parse)
E: The list of sources could not be read.
Go to the repository dialog to correct the problem.
E: _cache->open() failed, please report.

[/B][/I]Obviously, I screwed up something...*stupid, stupid, stupid... * Can someone please help me with this?[I][B]  [-o<

[/B][/I]RVcook

---

### Post by amingv on 2009-05-27
For the first part of the problem:

Make sure you're opening the file as root:

```
kdesudo kate /etc/apt/sources.list
```
if you're using KDE/Kubuntu or
```
gksudo kate /etc/apt/sources.list
```
if you're using Gnome/Ubuntu or XFCE/Xubuntu.

Also make sure Adept/Synaptic are not open while editing the file and that apt-get/aptitude are not running.

And for the second part:

There's an error in your sources.list file in line 54. Open the file and correct the error (press F11 in kate to see line numbers), or post line 54 here if you're not sure what the error is.

Also, who/what guide told you to add those lines? Most of them are by default in sources.list.

---

### Post by RVcook on 2009-05-27
Thank you for trying to help out!

Yes...I did open the file as root, and yes neither Synaptic nor Adept were open while I was doing this.  The problem now of course, is that neither wants to open since I did this!

Line 54 is:

[B][I]deb [http://ppa.launchpad.net/bogdanb/ppa/ubuntu/jaunty](http://ppa.launchpad.net/bogdanb/ppa/ubuntu/jaunty) main
[/I][/B]
I'm not sure what the error is...or how to fix, edit and/or remove it.

As for who told me, I got the information from the Kubuntu forums here:

[http://kubuntuforums.net/forums/index.php?action=printpage%3Btopic=3103718.0](http://kubuntuforums.net/forums/index.php?action=printpage%3Btopic=3103718.0)

I really appreciate any guidance you can give as to how to correct this. I hope this IS fixable...

RVcook

---

### Post by RVcook on 2009-05-27
The thread I posted was incorrect which I realized AFTER I clicked the submit button.  

To be honest, I searched through so many posts regarding Amarok, I can't remember exactly where I got that from.  I'll check and see if I can find it.  Sorry about that...

RVcook

---

### Post by amingv on 2009-05-27
Fix that line to read

[noparse]deb http://ppa.launchpad.net/bogdanb/ppa/ubuntu jaunty main[/noparse]

Notice the space between "...ppa/ubuntu" and "jaunty".

That should about fix the problem.

Can't see where in that article it told you to add the rest of the lines, but as long as you fix the "deb [http://ppa.launchpad.net/bogdanb/ppa/ubuntu](http://ppa.launchpad.net/bogdanb/ppa/ubuntu) jaunty main" one, the others shouldn't be a problem (they all look OK).

Try to save the file in kate again (it should work); if it doesn't, try to edit it in other editor, for example nano: in a terminal type

```
sudo nano /etc/apt/sources.list
```

Fix the line, save with Ctrl+O and exit with Ctrl+X.

Hope that helps.

EDIT:
Don't mind about the thread now, it's OK.
However, the next time you follow instructions from somewhere, make sure you make a backup of your working file in case anything goes amiss, you can do it like this:

> sudo cp /etc/apt/sources.list /etc/apt/sources.list.backup

---

### Post by RVcook on 2009-05-27
WhoooHoooo!!!!  It worked!  Thank you so much for the help.  It's hard to believe that one small 'space' can make that much of a difference.

I guess I'll just stick to things I know how to do and yes...in the event that I MUST do something like this again, I'll absolutely create a backup.

Your instructions were clear, precise and so very much appreciated.

Thanks again,

RVcook

---

### Post by amingv on 2009-05-27
> **RVcook said:**
> WhoooHoooo!!!!  It worked!  Thank you so much for the help.  It's hard to believe that one small 'space' can make that much of a difference.

I guess I'll just stick to things I know how to do and yes...in the event that I MUST do something like this again, I'll absolutely create a backup.

Your instructions were clear, precise and so very much appreciated.

Thanks again,

RVcook

Well, that's not exactly what i meant. If you stick to the things you know that wouldn't be much of a learning experience now would it? :)

Provided you make a backup, tinker as much as you please.

Glad the fix helped, BTW.

---

