---
title: "error in line of code"
date: 2009-04-29
forum: General Help
---

### Post by buggirlx on 2009-04-29
Please help with this problem. I got a free computer from accrc and it has the following problem.

When I go to add and remove programs I get this message:

“This is a major failure of your software management system. Please check for broken packages with synaptic, check the file permissions and correctness of the file '/etc/apt/sources.list' and reload the software information with: 'sudo apt-get update' and 'sudo apt-get install -f'.”

When I go to synaptic package manager I get this error:

E: Malformed line 58 in source list /etc/apt/sources.list (dist parse)

E: The list of sources could not be read.

Go to the repository dialog to correct the problem.

E: _cache->open() failed, please report.

---

### Post by taurus on 2009-04-29
There is something wrong with line 58 in /etc/apt/sources.list.

Applications -> Accessories -> Terminal
```
gksudo gedit /etc/apt/sources.list
```

---

### Post by fdrake on 2009-04-29
can you post your copy of your souce file:
```
sudo gedit /etc/apt/sources.list
```

---

### Post by buggirlx on 2009-04-29
ok, so I just go in there and type that in?

---

### Post by taurus on 2009-04-29
The command above would allow you to edit /etc/apt/sources.list with root privilege.  You need to see what is wrong with line 58 though.

---

### Post by fdrake on 2009-04-29
> **buggirlx said:**
> ok, so I just go in there and type that in?

you type the command into the terminal and a new window will open(a text editor prog.)copy the text of the file and past it in the next post of this thread so we can understand whats wrong.

---

### Post by buggirlx on 2009-04-29
This is what came up, but I don't see line 58
# deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) hardy main restricted
# deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) hardy-updates main restricted
# deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) hardy-security main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy universe
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy-updates universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy multiverse
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy-updates multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) hardy-backports main restricted universe multiverse
# deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) hardy-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) hardy partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) hardy partner

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy-security main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy-security main restricted
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy-security universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy-security universe
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy-security multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy-security multiverse
deb [http://archive.ubuntu.com/ubuntu/pool/restricted/l/linux-restricted-modules-2.6.24/](http://archive.ubuntu.com/ubuntu/pool/restricted/l/linux-restricted-modules-2.6.24/) nvidia-glx_96.43.05+2.6.24.16-23.56_i386

---

### Post by lisati on 2009-04-29
Suggestion: when including listings from your files in your posts, put [noparse]```
[/noparse] at the start ant [noparse]
```[/noparse] at the end. This can help make it easier to read.

---

### Post by mb_webguy on 2009-04-29
Line 58 is the last line in the file.```
deb http://archive.ubuntu.com/ubuntu/pool/restricted/l/linux-restricted-modules-2.6.24/ nvidia-glx_96.43.05+2.6.24.16-23.56_i386 
```
That's... not a valid source line.  Delete it, and you'll be fine.

---

### Post by buggirlx on 2009-04-29
Ok, but this case there is only that, I just wrote the first line myself to say, that is what it is.

---

### Post by buggirlx on 2009-04-29
Thanks I deleted the line and now the software has showed up, but why does not have a list to tell me that it is line 58, otherwise you just count all the lines?

---

### Post by fdrake on 2009-04-30
if you re-type the commands we suggested you to open the source file, gedit (the text editor) will show you the coordinates of the cursor on your text at the bottom of the window. it will say line Y and colon X. in this way you don't need to count

---

### Post by mb_webguy on 2009-04-30
Many text editors, including gedit, have the ability to display line numbers.  In gedit, you'd go to Edit->Preferences, and check the box next to "Display line numbers".

With nano, you have to call it with the "-c" option (e.g. "sudo nano -c /etc/apt/sources.list"), and the line number is shown just above the menu.

---

### Post by buggirlx on 2009-04-30
I added some programs, but I am looking for more is there a url in which I can view more programs for this system?

---

### Post by buggirlx on 2009-04-30
ok, but how to I get to the gedit place?

---

### Post by mb_webguy on 2009-04-30
> **buggirlx said:**
> I added some programs, but I am looking for more is there a url in which I can view more programs for this system?Add/Remove Applications (Applications->Add/Remove...) will show you all of the applications available in the repositories.  Synaptic Package Manager is a more powerful version of Add/Remove Applications that will show you all of the individual software packages (including non-application software, such as libraries) available in the repositories.  Most software you could want to install is available in the repositories, and it's almost always best to install software through the repositories if it's available.

If you know of a specific piece of software you want and either isn't in the repositories or else the version in the repositories isn't the one you want, you can search [Launchpad]("https://launchpad.net/") for a PPA containing the software.  A PPA is essentially a mini-repository.  Once you've added a PPA to your software sources, you can install and update software in the PPA using Add/Remove or Synaptic, just as you would software from the official repositories.

Another place to look for software is [GetDeb]("http://www.getdeb.net/").  GetDeb is a communal archive for software packaged by other users.  To install software from GetDeb, you would download the deb file, and double-click on it in Nautilus.

---

### Post by mb_webguy on 2009-04-30
> **buggirlx said:**
> ok, but how to I get to the gedit place?

gedit is the default text editor for Ubuntu (Applications->Accessories->Text Editor).  You would open it from the terminal using "gedit *filename*".

---

### Post by buggirlx on 2009-04-30
I looked at the place, but there is a lot how does one sort the software? I am looking for a music program that allows one to see the inside of the song such as sound forge type of programs and something that might work like Dreamweaver and something I read about that allows one to convert music from a cd to the notes for playing that could be then printed. I remember a list from something that was before ubuntu years ago.

---

### Post by zacktu on 2009-04-30
Another way to see lines by number is to use pr (the print command).  For example,

pr -n /etc/apt/sources.list | more

will let you see a screenful of numbered lines at the time.  Press the space bar to see the next screenful.  Press "q" to exit.

---

### Post by mb_webguy on 2009-04-30
> **buggirlx said:**
> I looked at the place, but there is a lot how does one sort the software? I am looking for a music program that allows one to see the inside of the song such as sound forge type of programs and something that might work like Dreamweaver and something I read about that allows one to convert music from a cd to the notes for playing that could be then printed. I remember a list from something that was before ubuntu years ago.

In Add/Remove, you can sort by type of program on the left, and by source at the top.  I'd suggest setting the drop-down box at the top to "All available applications".

For the audio editor, try Audacity (not Audiacious, which is a music player).

For a WYSIWYG html editor, the most popular is probably Kompozer, though I've seen Amaya, SeaMonkey and Quanta Plus suggested.  OpenOffice is also capable of WYSISYG html editing -- just create a document and save it as html.

As for the sheet music part, LilyPond (and RoseGarden, which I think uses LilyPond) will convery midi files to sheet music.  To convert CD audio to sheet music, you'd first have to convert it to midi using something like [WaoN]("http://waon.sourceforge.net/").

---

### Post by buggirlx on 2009-05-01
That you for all your help.

---

### Post by buggirlx on 2009-05-01
Audacity now installed and working.

---

### Post by buggirlx on 2009-05-01
I am not able to get what I wanted out of ubuntu software, wanted to delete post, but it won't let me.

---

