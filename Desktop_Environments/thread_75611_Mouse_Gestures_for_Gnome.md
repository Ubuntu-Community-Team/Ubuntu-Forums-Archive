---
title: "Mouse Gestures for Gnome"
date: 2005-10-13
forum: Desktop Environments
---

### Post by gflores on 2005-10-13
Is there a mouse gestures application for Gnome?

---

### Post by Kasanax on 2006-01-05
I've been looking for the same thing... ever since I've started using the FireFox All-In-One Gestures extension, I find myself trying to do mouse gestures outside of FF too.... 

I found this thread a few minutes ago, but I haven't gotten a chance to take a look at any of the mentioned packages yet. 

[http://www.ubuntuforums.org/showthread.php?t=90111&highlight=mouse+gestures](http://www.ubuntuforums.org/showthread.php?t=90111&highlight=mouse+gestures)

Let me know if you find out anything!

---

### Post by zorglub on 2006-01-07
[QUOTE=Kasanax]I've been looking for the same thing... ever since I've started using the FireFox All-In-One Gestures extension, I find myself trying to do mouse gestures outside of FF too.... [/QUOTE]

Besides Firefox, Epiphany Web Browser supports a mouse gesture extension...

Still looking for outside too ;)

---

### Post by Kasanax on 2006-01-07
I tried using WayV (there's a mention of it in the thread that I posted a link to earlier)...

After playing around with it for a little while, I decided it wasn't worth the effort just yet. It looks like it's still in a  pretty rough development phase, and I think I'll just go without until I can find something better.

If you're desperate for a gestures app, though, it might work. - It's available in the Universe repositories.

---

### Post by Sef on 2006-01-07
The Opera browser also supports mouse guestures.

---

### Post by 23meg on 2006-01-07
xstroke is a full screen gesture recognition program mostly used for text input (basic handwriting recognition) but it may (already?) be extended to perform operations of any kind based on the input it gets.

---

### Post by manatlan on 2006-03-03
i'd installed your deb : it works well
i can write chars ;-)

is xstroke able to run a program with a stroke ? or maximize the current window ?
it seems it can't ;-( ... i'm not able to find any solution

---

### Post by JackandJohn on 2006-05-03
Somebody really needs to look into this; mouse gestures look and sound funny at first, but once you realize just how amazingly amazing they are, there is no going back ("I have to drag the cursor all the way to the close button? ffs!")

I do alot of windows and alot of file stuff: I have "strokeit" fully configured in windows, but nothing else in ubuntu compares. Honestly, I would be more excited about a gesture program that was lightning fast, easily configurable, and universal, than I would about XGL


I hate not knowing how to program, and not having the time to start.
All we really need to do is get some of the good devs using mouse gestures for a couple weeks, and it will be top priority ;)

---

### Post by tribaal on 2006-05-03
Didn't have the opportunity to test it, but this seems to be what you're looking for... [link]("http://www.stressbunny.com/wayv/").

- trib'

---

### Post by grizzly on 2006-07-13
> **JackandJohn said:**
> Somebody really needs to look into this; mouse gestures look and sound funny at first, but once you realize just how amazingly amazing they are, there is no going back ("I have to drag the cursor all the way to the close button? ffs!")

I do alot of windows and alot of file stuff: I have "strokeit" fully configured in windows, but nothing else in ubuntu compares. Honestly, I would be more excited about a gesture program that was lightning fast, easily configurable, and universal, than I would about XGL


I hate not knowing how to program, and not having the time to start.
All we really need to do is get some of the good devs using mouse gestures for a couple weeks, and it will be top priority ;)

Hello?? are you my clone? My thoughts on mouse gestures are *exactly* like yours, the whole mouse gestures are amazing thing, top priority thing, going all the way to the close button == murderous!! 
Oh somebosy(devs) try mouse gestures ( strokeit on windows ) plzzzzzzz

---

### Post by dpm on 2006-07-14
> **grizzly said:**
> Hello?? are you my clone? My thoughts on mouse gestures are *exactly* like yours, the whole mouse gestures are amazing thing, top priority thing, going all the way to the close button == murderous!! 
Oh somebosy(devs) try mouse gestures ( strokeit on windows ) plzzzzzzz

I think many people think the same.

BTW, StrokeIt is the only one software I miss from Windows. I knew it wouldn't work, but I even tried to run it under wine...

---

### Post by dpm on 2006-07-14
I tried wayv some time ago and today I gave it another go, but I never got it to work. Reading the man page and the help for wayv.conf, it seems quite easy, but I never got it to recognise or give visual feedback of any gestures under GNOME.

Is anyone here actually using it?

---

### Post by shrimpney on 2006-07-26
Hey people... my first post, and it's about mouse gestures - that's how important I feel they are!

I'm a recent convert from Windows to Ubuntu (a couple of weeks) and so far I am absolutely LOVING the experience.  The one and only thing I am missing is [StrokeIt]("http://www.tcbmi.com/strokeit/") and its global mouse gestures.

Thanks for noting wayV.  I'm going to give it a try and will report back, but from the changelog it doesn't look like there's been any recent activity on the project.

---

### Post by shrimpney on 2006-07-26
OK, here's my report on wayV after playing around with it for an hour or so.

Pros:
[LIST]
[*]The configuration file for 0.3 is clean and intuitive and is actually easier to work with than StrokeIt's configuration.
[*]It reports the mouse gestures it recognises as you draw them.
[*]It does actually work... sort of.
[/LIST]

Cons:
[LIST]
[*]It's not very good at determining the direction ('vector' in wayV terminology) of the gesture you're drawing. For example 'click-drag left' and 'click-drag right' are often interpreted as the same gesture - this makes the program all but unusable for the basics of web browsing!
[*]It's way too forgiving when trying to match your mouse movement to a gesture - it's almost impossible, for example, for wayV to determine between a 'J' and a '>', with the result that you're never quite sure what it's going to do.
[*]It takes over the control of your mouse button completely - there's no timeout after which the 'normal' button function is restored.
[/LIST]

In summary, it's *very* close to being there, and with a few adjustments it could be the real deal.

I'd be interested in hearing other people's experiences with the program.  Don't forget, if you're planning to give wayV a spin yourself, that the right mouse button is "button 3"!

Perhaps if we stir up enough interest we could get the developers interested in the project again...?

---

### Post by JackandJohn on 2006-09-04
Honestly, as a long-term goal, I would like to see the input method adbstracted from the keyboard and mouse altogether, so that plugins for different types of input can be written, and nothing else would need to be recoded (for legacy support)

Basically so that mouse, keyboard, tablet, joystick, gestures, etc are all treated equally by the OS itself; evdev would be a good starting point for something like that; it takes raw messages, and decides what to do with them.


Like we say; we need the devs getting some strokeit action, and I can almost guarantee you there would be some activity on a gesture project

---

### Post by JackandJohn on 2006-09-04
> **shrimpney said:**
> OK, here's my report on wayV after playing around with it for an hour or so.

Great stuff; thank you.. I tried picking up wayv when I first switched, and could never get it working.. Now I know I should wait for a while ;)

---

### Post by grizzly on 2006-09-11
hmm wayv is ok, works in a sort of way. But the main problem that I have observed is that ll moouse gesture apps have an irrestible tendency to have human readable text files, which is why ALL mouse gest apps rely on the very inferior telephone grid method of recognizing gestures, unlike opera and strokeit

---

### Post by sbfisher on 2006-10-21
I agree about mouse gesture support at the entire GUI level.  It is one of the most useful, time saving things ever.  Minimizing/maximizing/restoring/next/back/closing are the gestures I use a ton, and not just in a web browser, but also in file browser or any program (especially min/max/restore).

Some base code seems to be out there with wayv (which I agree is sorely lacking, but it demonstrates that something can be done in the way of mouse gestures in Linux). I'm certain someone has better recognition code (like the mozilla or opera code).

Seems like the code could be fixed up by someone who knew what they were doing and Ubuntu would be usable in this way.  This is seriously a deal breaker for me in using Ubuntu since mouse gestures are a huge time saver.  I agree about StrokeIt in Windows, I cannot use a computer without it installed.  The author got most parts really right: from intuitive commands (like a C shape for close, up diagonal for maximize), to the timeout for going back to a normal context menu, to good recognition. Definitely whips butt all over anything available in Linux.  It would be cool if the developer did a port (though that's probably not likely to happen).

Gestures are a killer utility. I'm convinced the reason they're not more popular is that not enough people know about them and use them. And most of the programmer types in Linux consider shell prompt to be the only way to accelerate anything so they don't bother to work on the GUI technologies. "Real men don't use GUIs" seems to be their motto." </rant>

---

### Post by olejorgen on 2006-11-23
Hm.. if someone does not get wayv to work, be sure to start it like this: wayv /etc/wayv.conf
ie. You must supply a config file (it appears)

EDIT: Well, it seems it's not actually working (I donæt get any visual feedback), but it responds to changes in the configfile.

---

### Post by frafu on 2007-01-14
I think Kubuntu gets shipped with mouse gesture software; under Settings->Input there are Mouse Gestures. I have not tried it yet and don't know how well it works. 

I suppose: Those that want to give it a try can install the kubuntu-desktop metapackage for example by using the Synaptic Package Manager from Ubuntu and choose the kde desktop when logging in. Of course, this way we are not using gnome anymore, but kde. 

frafu

---

### Post by frafu on 2007-01-14
Hello, 

For your information: I have written a specification about mouse gestures. It is the fourth part (mousetweak #4)  of a more general specification about enhancing the functionalities of the pointer also from the point of view of accessibility for disabled people. 

The specification is located on the wiki at the following address: 
[https://wiki.ubuntu.com/Accessibility/Specs/MouseTweaks?action=show](https://wiki.ubuntu.com/Accessibility/Specs/MouseTweaks?action=show)

I have also started a thread for comments to the mousetweaks specification; here it is:
[http://ubuntuforums.org/showthread.php?p=2012703](http://ubuntuforums.org/showthread.php?p=2012703)

Finally, I will also present the mousetweak specification to the ubuntu-devel-discuss mailing list:
[https://lists.ubuntu.com/mailman/listinfo/ubuntu-devel-discuss](https://lists.ubuntu.com/mailman/listinfo/ubuntu-devel-discuss)

Any comments or suggestion is welcome. 

Have a nice day. 

frafu

---

### Post by cosimo on 2007-01-14
Hello,
 there is indeed a mouse gesture application for gnome named "wayv". 
 I didn't read through the whole post so if already mentioned forget it.
 HOWEVER, since dapper it has not worked in ubuntu easily. IT used to be just a matter of installation and use. Having been in contact with the developer and him testing it even he has not been able to understand why it doesn't work on some system since he got it to work on edgy default install.
there is  setting suggested by him, but that didn't work either.
 if you get this to work it is a great application , making mouse gestures systemically instead of application dependent is great.

---

### Post by frafu on 2007-01-14
@cosimo

Thanks for the reply. The wayV application was already talked about in this thread, and by reading the comments it does not seem to work rreliably enough to be useful. 

Maybe it can be fixed; maybe part of it can be used to create a better mouse gestures application; maybe a complete new approach is necessary... Unfortunately, I don't know. 

Anyway, thanks for the comment and particularly for letting me know about your interest in mouse gestures software. 

Have a nice day. 

Francesco

---

### Post by cosimo on 2007-01-28
I did want to add this.
 I have several clients who are dependent on wayv, however, it has not run since breezy. When dapper final came out and all thorugh edgy and now feisty, everyone, except one individual I have spoken with has gotten this to run.
 It runs flawlessy if you create a separate root account log out of user account and log into root account. No problems however in the user account it will not work at all.
  I have discussed this wiht the develper an dhe apparentlu got it to work on edgy as well, but the several people ai have talked with have the same problem I do.
 I need to get this to work on edgy and feisty if my clients are to upgrade their systems
so anyone with any solutions please let me know.

---

### Post by Icarosaurus on 2007-02-01
I tried to compile wayV under Feisty and all went fine...
I did the same simple steps under Edgy...and wayv doesn't work...
WHY?
anyone had the same issue?
thanks in advance

---

### Post by LycoLoco on 2007-02-12
Frafu - how would one go about using these accessibility features in 6.10? I'd love to try out what you guys have coded, even if it's just like beta testing. Thanks!

---

### Post by frafu on 2007-02-13
@Lycoloco

There already are a few accessibility features in ubuntu. You can find them under: 

- Menu Applications->Accessibility 

- Menu System->Preferences->Assistive Technology Preferences

If you are looking for mouse gestures software, I don't know whether there is something that works reliably enough. 

kmousetool from kubuntu also works under ubuntu; it is a software to let the computer click automatically without the user pressing the mouse button 

The features defined in the following specification have been delayed to feisty+1
[https://wiki.ubuntu.com/Accessibility/Specs/MouseTweaks?highlight=%28mousetweaks%29](https://wiki.ubuntu.com/Accessibility/Specs/MouseTweaks?highlight=%28mousetweaks%29)

As far as I know, for the moment the development is mainly concentrating on visual impairment and on making gdm accessible. 

You can learn more about it in the 
- Accessibility Forum on this board: [http://ubuntuforums.org/forumdisplay.php?f=145](http://ubuntuforums.org/forumdisplay.php?f=145)
- on the wiki: [https://wiki.ubuntu.com/Accessibility/](https://wiki.ubuntu.com/Accessibility/)
- on the Accessibility Mailing lists: [https://lists.ubuntu.com/mailman/listinfo/](https://lists.ubuntu.com/mailman/listinfo/) especially
[https://lists.ubuntu.com/mailman/listinfo/ubuntu-accessibility](https://lists.ubuntu.com/mailman/listinfo/ubuntu-accessibility)
[https://lists.ubuntu.com/mailman/listinfo/ubuntu-accessibility-devel](https://lists.ubuntu.com/mailman/listinfo/ubuntu-accessibility-devel)
- channel #ubuntu-accessibility on irc.freenode.net in Internet Relay Chat (IRC)

Francesco

PS: Maybe that I should point out that I am not a developer...

---

### Post by cudjoe on 2008-01-10
I just found Gestikk at Gnome-files :
[http://gnomefiles.org/app.php/Gestikk_Mouse_Gesture_Recognition](http://gnomefiles.org/app.php/Gestikk_Mouse_Gesture_Recognition)

...still have to try it.

---

