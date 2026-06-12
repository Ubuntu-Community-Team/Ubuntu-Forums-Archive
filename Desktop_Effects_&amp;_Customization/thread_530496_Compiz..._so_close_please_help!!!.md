---
title: "Compiz... so close please help!!!"
date: 2007-08-20
forum: Desktop Effects &amp; Customization
---

### Post by Parms on 2007-08-20
OK, after finally finding somewhat of a clue as to what I'm doing, I tried about 5-6 different forum topics to get as far as I did. Before I couldn't get anything to run...

Now I'm at the point where I can open CompizConfig... I can see and edit all the options.

Yet nothing is happening to my computer. Like when I enabled wobbly windows, nothing happens. Also I'm trying to get the cube to work with no avail. And I can also select a theme from emerald and that won't work either. This is what I did...


Quote:
Originally Posted by Ub1476 View Post
I suppose you used this script: Link

It's not wroking for me neither, and I have an ATI card as well.. If you don't find a fix I recomend you to uninstall (run the script choose install, then uninstall), then delete the .compizconfig folder in your home directory (ctrl+h to show hidden files) then do:

Code:

sudo apt-get autoremove

apt-get clean

Now follow this Guide.

After you have installed CF, install Emerald too:

Code:

sudo apt-get install emerald emerald-themes

Now press ctrl+F2 and launch CF with:

Code:

compiz --replace -c emerald

( if it doesn't work, you can try "compiz --replace" instead.

Hope that fix it.
I successfully did everything up to the ctrl+F2 part. Do you mean alt+F2. Anyways I tried those command lines and nothing happens. This is what I've got now...

I can succesfully open compizconfig. I can select and deselect things, yet nothing is happening to my windows, etc..

Is there anything else I have to do to get this to start when ubuntu starts? I mean the same settings each time?


Errrr.... This is really frustrating. Am I better off just installing a different version of the OS.

I'm using 64bit 7.04 all updates are done, and I followed the above guide to a tee. When It says to start compiz with the Alt+F2 key and I type those command lines in, nothing happens. I mean visually. before I would get an error, but now nothing. Please help before I throw my beautiful laptop across the room in utter frustration!!!

P.S. I wouldn't really do that :confused::confused::confused:

---

### Post by loserboy on 2007-08-20
are you using an ATi card, if so did you get the right drivers and have 3D acceleration enabled?

---

### Post by Parms on 2007-08-20
I followed this guide [http://ubuntuforums.org/showthread.php?t=414194](http://ubuntuforums.org/showthread.php?t=414194)

These are the steps I took ...
Installed ubuntu... everything worked.

I went to..
System >> Administration >> Restricted Drivers Manager

Clicked enable..
It started installing something.

Now says...
Enabled .. In use

I can run compizconfig and can enable and disable items
System >> Preferences >>CompizConfig Settings Manager

I can also run it from the Alt+F2 and from the terminal...

Everything works till this point....

For some reason I get this...

parms@parms-laptop:~$ compiz --replace -c emerald
Fatal: Failed test: texture_from_pixmap support
Checks indicate that it's impossible to start compiz on your system.

parms@parms-laptop:~$ compiz --replace
Fatal: Failed test: texture_from_pixmap support
Checks indicate that it's impossible to start compiz on your system.
parms@parms-laptop:~$ 

I tired the commands in Alt+F2 but nothing happened so I ran in the terminal to see what the exactly was going on. 

I'm hopping that it's just a driver problem and nothing more. I'm a n00b and don't know where to go to fix this, and assumed that when I enabled it, it downloaded all the neccesary items. 

This is my card.. ATI Radeon Xpress 200M
Running AMD turion 64 .. 64 bit ubuntu 7.04

If someone can help me with the drivers or verify that this card works that would help. I'm assuming the card works since it plays all the available 3D games in US market.

Thanks in advance.

---

### Post by miggols99 on 2007-08-20
ATI cards are really annoying to set up. You will have to install XGL. You will find a howto on the howtos and tutorials forum. Had a look a round and your card doesn't support 3D with the open source driver. Looks like your stuck with using XGL. AIGLX is much easier to set up. For future reference never buy ATI. Their drivers for Linux are really bad. Nvidia and Intel are much better.

---

### Post by Parms on 2007-08-20
> **miggols99 said:**
> ATI cards are really annoying to set up. You will have to install XGL. You will find a howto on the howtos and tutorials forum. Had a look a round and your card doesn't support 3D with the open source driver. Looks like your stuck with using XGL. AIGLX is much easier to set up. For future reference never buy ATI. Their drivers for Linux are really bad. Nvidia and Intel are much better.

I've started looking into XGL and someone gave me a post to try, Anyway didn't plan on running linux when I bought my computer. I thought ATI was decent, I refused to buy a SONY laptop for a Nvidia card. Where I live HP only had ATI cards in the laptops. My main computer which I built is running Nvidia :)

---

### Post by Ub1476 on 2007-08-20
I answered your message, check it out;)

---

### Post by Parms on 2007-08-20
I followed steps from this guide... Method A

[https://help.ubuntu.com/community/CompositeManager/Xgl](https://help.ubuntu.com/community/CompositeManager/Xgl)

When I log out and log back in with the XGL session my screen is like a small grid, with an X for my mouse pointer. I pressed esc after awhile to get back to my normal log in screen. 

Hmmm... 

Do I need to try method B? If so do I need to undo anything I did with method A?

---

### Post by Parms on 2007-08-20
OK ... I logged into an XGL session and waited for the weird screen to disappear. Now I can see my desktop but it is all funny looking, like hyper blurred or something to that effect, ????

---

### Post by Ub1476 on 2007-08-20
No, no reason in using method B. Just so you know, the login has a backgroudn with loads of x' and a x cursor. Although after 2 seconds it should be gone. Try the link I gave you. Worked for mine AMD64.

---

### Post by Ub1476 on 2007-08-20
Can you post a screenshot (if possible)?

---

### Post by mysticmatrix on 2007-08-20
Parms, you have made atleast 3 post on same problem. Please don't do this. If anyone knows the answer, they will help. And frankly much can't be done on ATI.

---

### Post by Parms on 2007-08-20
OK, I'll try the link you gave me. Althought isn't beryl different then compiz? Either way the method A did work and the weird screen as mentioned above disapperead. And went to my desktop. 

But the desktop is like F***ked up. Like Its all lined out or something, Luckily I know where the logout button is. Either way is there a reason why my screen doesn't look normal in XGL like it did with gnome?

Also now when I goto
System >> Administration >> Restricted  Drivers Manager

It says I dont have any restricted drivers anymore. ??? Hmmm... 

I'm so lost... I know you guys are helping me a lot and I really appreciate it. When it seems I get one step closer I'm taken two steps back.

---

### Post by Parms on 2007-08-20
> **Ub1476 said:**
> Can you post a screenshot (if possible)?

Don't know how to do that yet, and wouldn't know how to navigate anything in XGL. SInce I can't see. 

Hopefully this explains it...

Log in window normal...

I click options... XGL...

Then I log in.

This session only.

Ok the notorious scary screen with the grid and the X.

Waited 2 seconds.

OK >> I see my desktop it looks like my one from gnome, but is blured. With the colors lined out like tracers. Horizontally. I know where some icons are so I opened terminal and it looks funny, and the text is un readable. Then when I closed terminal it's outline was still embeded on my screen.

---

### Post by Ub1476 on 2007-08-20
Alright..

Try this:

```
glxinfo | grep direct
```

If direct rendering comes out as yes, I'm lost.

If it's no, your 3d isn't working properly.

Anyway, you might have to reinstall your system, only takes bout 30 minutes though, then follow the links I provided. I also recommend you to follow this guide when X won't start from live CD: [Install Ubuntu when X cannot start.]("http://ubuntuforums.org/showthread.php?t=448809&highlight=feisty+fawn")

Just so everything is added in one place:

Put in Live CD, when X wont start, follow this guide: [Link]("http://ubuntuforums.org/showthread.php?t=448809&highlight=feisty+fawn")

When everything is installed and configured, install XGL: [Link]("http://ubuntuguide.org/wiki/Ubuntu:Feisty#Install_Beryl_using_proprietary_FGLRX_drivers_from_ATI") (Do NOT install Beryl (stop were you add sources)

Then Compiz-Fusion for AMD64 systems: [Link]("http://www.compiz.org/Compiz_and_Copmiz_Fusion_GIT_Ubuntu_Repository#amd64")

Hope it works.

---

### Post by Parms on 2007-08-20
> **Ub1476 said:**
> Alright..

Try this:

```
glxinfo | grep direct
```

If direct rendering comes out as yes, I'm lost.

If it's no, your 3d isn't working properly.

Anyway, you might have to reinstall your system, only takes bout 30 minutes though, then follow the links I provided. I also recommend you to follow this guide when X won't start from live CD: [Install Ubuntu when X cannot start.]("http://ubuntuforums.org/showthread.php?t=448809&highlight=feisty+fawn")

Just so everything is added in one place:

Put in Live CD, when X wont start, follow this guide: [Link]("http://ubuntuforums.org/showthread.php?t=448809&highlight=feisty+fawn")

When everything is installed and configured, install XGL: [Link]("http://ubuntuguide.org/wiki/Ubuntu:Feisty#Install_Beryl_using_proprietary_FGLRX_drivers_from_ATI") (Do NOT install Beryl (stop were you add sources)

Then Compiz-Fusion for AMD64 systems: [Link]("http://www.compiz.org/Compiz_and_Copmiz_Fusion_GIT_Ubuntu_Repository#amd64")

Hope it works.


parms@parms-laptop:~$ glxinfo | grep direct
Xlib:  extension "XFree86-DRI" missing on display ":0.0".
direct rendering: No
OpenGL renderer string: Mesa GLX Indirect
parms@parms-laptop:~$ 

ok, Maybe I'll retry from scratch.
Also when I install from cd.. I have no problems.

---

### Post by Ub1476 on 2007-08-20
Sorry, thought you did since you said you used this guide: [Link]("http://ubuntuforums.org/showthread.php?t=414194")

---

### Post by mysticmatrix on 2007-08-20
> **Parms said:**
> parms@parms-laptop:~$ glxinfo | grep direct
Xlib:  extension "XFree86-DRI" missing on display ":0.0".
direct rendering: No
OpenGL renderer string: Mesa GLX Indirect
parms@parms-laptop:~$ 

ok, Maybe I'll retry from scratch.
Also when I install from cd.. I have no problems.

Well I guess you have uninstalled ATI drivers in frenzy.

The course of action would be:
A)Install the ATI Drivers.
A1)Check you have direct rendering enabled by use of glxinfo
B)Install XGL and log into it.
C)Run Compiz.

---

### Post by Parms on 2007-08-20
> **Ub1476 said:**
> Sorry, thought you did since you said you used this guide: [Link]("http://ubuntuforums.org/showthread.php?t=414194")

I did that after I was in gnome.. Thought I needed it for my ATI drivers.

Can you please copy and paste the section where I'm suppose to stop. I don't know what sources your referring to.

---

### Post by Parms on 2007-08-20
> **mysticmatrix said:**
> Well I guess you have uninstalled ATI drivers in frenzy.

The course of action would be:
A)Install the ATI Drivers.
A1)Check you have direct rendering enabled by use of glxinfo
B)Install XGL and log into it.
C)Run Compiz.

OK.. don't know how I uninstalled them. Here is the plan I hope it works. I have two computers, so I can still use online as a reference. I'm going to do a fresh install.. This is my plans.. correct me if there is something wrong or missing..

1) Fresh install...
2) Install ATI drivers (should I use envy, or just enable the restricted drivers and download it that way)
3)install XGL
4)install compiz
5)log into XGL with compiz

hopefully that works.

---

