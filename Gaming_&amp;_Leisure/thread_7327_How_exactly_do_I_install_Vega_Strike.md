---
title: "How exactly do I install Vega Strike?"
date: 2004-12-06
forum: Gaming &amp; Leisure
---

### Post by inha on 2004-12-06
I installed the data and music files with synaptic but can't quite figure out how to move on from here. I tried the installer script too but my system is missing some developement tools. It wouldn't be a big deal to get those and try it again but I'd rather get it via a package manager for uh... package manageability. Or something.

---

### Post by timeoff on 2005-01-10
Any joy on how to get this going after downloading the data and music files?

T

---

### Post by Marquis_de_Carabas on 2005-01-12
This looks like such a cool game (I *loved* the original Elite) that I've tried to install it several times starting from back before I used Ubuntu. I could never get it working though (I'm a bit of a Linux noob, although I have installed several programs from source) so I decided to wait until they finish the 'easy installer'. Mind you, I could also try the Windoze version through Cedega. Hmm...

---

### Post by Marquis_de_Carabas on 2005-01-12
Yep, Vega Strike installed - and so far plays - perfectly with Cedega 4.2. Haven't tried it with WineX (the free version), but should be worth a try for anyone who just can't get the Linux version working.

---

### Post by poster_nutbag on 2005-01-15
I applaud your efforts in getting VegaStrike running on Cedega, but it does seem a little silly when there is a perfectly good Linux version avaliable. I'm going to try and install this myself and see what I get...

---

### Post by jakeslife on 2005-01-15
I've tried installing the linux version and couldn't get it to work.

---

### Post by Marquis_de_Carabas on 2005-01-21
> I applaud your efforts in getting VegaStrike running on Cedega, but it does seem a little silly when there is a perfectly good Linux version avaliable.

I completely agree, and I haven't given up on getting the Linux version to run, I just wanted to spend a leetle time playing the game rather than fighting to install it  :)

---

### Post by Perfect Storm on 2005-01-21
The people behind Vega strike did release a new vega strike installer, I havn't tried yet, but it's something you have to download along with vega strike.

As I understood from what I read, you have to put the new installer into the source folder and run it through there instead of using the normal  running scripts.



Edit: found it, [http://vegastrike.sourceforge.net/forums/viewtopic.php?t=3244](http://vegastrike.sourceforge.net/forums/viewtopic.php?t=3244)

---

### Post by Perfect Storm on 2005-01-24
Okay I've figure out how to install Vega Strike.

You'll need to download through CVS also if you do that you'll get the most updated Vega Strike (newer than the released 0.4.2 version)

First
install **libopenal0**,**libopenal-dev**,**python2.3-openal** and **cvs** from Synaptic Package Manager.

Then
[Download CVS script file here](http://vegastrike.sourceforge.net/files/linux_vegastrike-0.4.2.sh) 

Then grab the attached files I've added in this post and rename it to glext.h

[b]cd /where/the/glext.h/file/is
sudo cp glext.h /usr/include/GL[/b]

Now
[b]cd /where/you/saved/the/CVS/Script
sudo sh linux_vegastrike-0.4.2.sh[/b]

Grab a cup of coffee and relax an hour or so.
When it's done, write:

**sudo vslauncher**

VOILA!!!!


.:=The AI Dude=:.

EDIT: The only problem is you have to run it as root (sudo) and I havn't manage to enter game settings yet. But it's still playable though it is in the development phase.

EDIT, EDIT: hmmm...it seems that something wrong with Attachment the file so I post the link,  [http://oss.sgi.com/projects/ogl-sample/ABI/glext.h](http://oss.sgi.com/projects/ogl-sample/ABI/glext.h) 
Press the 'file' tab and 'save page as' and press the save button.

---

### Post by Perfect Storm on 2005-01-24
Here's a screenshot :)

---

### Post by Perfect Storm on 2005-01-24
Okay found out to bypass the 'Game Setting' option, just:

sudo /usr/local/share/vegastrike/data/vssetup

---

### Post by paul cooke on 2005-02-06
[QUOTE=Artificial Intelligence]

EDIT: The only problem is you have to run it as root (sudo) and I havn't manage to enter game settings yet. But it's still playable though it is in the development phase.

EDIT, EDIT: hmmm...it seems that something wrong with Attachment the file so I post the link,  [http://oss.sgi.com/projects/ogl-sample/ABI/glext.h](http://oss.sgi.com/projects/ogl-sample/ABI/glext.h) 
Press the 'file' tab and 'save page as' and press the save button.[/QUOTE]

You may find that you are having to run as sudo because you have not made yourself a member of the video group. I discovered I couldn't get GL based stuff to run at all for my normal username, but the first username I created runs stuff fine. I investigated using the user manager in the computer menu and made sure my normal user had the same group memberships.

---

### Post by Perfect Storm on 2005-02-06
Thanks for the reply.


I managed to run it as non-root. I discovered a /.vegastrike in home folder which was only allowed root-access. So I simply 'chmod' the folder.



.:=The AI Dude=:.

---

### Post by paul cooke on 2005-02-08
vegastrike is in hoary... :) upgraded last night :D

---

### Post by Perfect Storm on 2005-03-06
Vega Strike 0.4.3 is out!

---

### Post by dolny on 2005-05-12
Downloaded Vega Strike and fought with it for an hour... cannot install due to dependencies. I'm so pissed off. :(

I used these 3 packages: (tried to use it):

vegastrike_0.4.3-1_i386.deb
vegastrike-data_0.4.3-2_all.deb
vegastrike-music_0.4.3-1_all.deb

For example:
> The following packages have unmet dependencies:
vegastrike-data: Depends: vegastrike (>= 0.4.3-1) but it is not going to be in                                                                                                  stalled Depends: vegastrike (< 0.4.4-1) but it is not going to be ins                                                                                                  talled E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).

Uhhh... I would love to test this game :(

---

### Post by blackmatter69 on 2010-09-19
nothing for me

---

### Post by Juvencio on 2012-08-29
[install]("http://www.playdeb.net/updates/ubuntu/12.04/?q=Vega+Strike#how_to_install")

---

