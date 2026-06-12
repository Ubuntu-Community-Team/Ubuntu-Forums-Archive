---
title: "Guide: Re-enabling &quot;Genie Effect&quot; using &quot;Magic Lamp&quot;"
date: 2007-09-22
forum: Desktop Effects &amp; Customization
---

### Post by FunkyRider on 2007-09-22
Version 0.5.5~git20070921+3v1ubuntu0 (or maybe the ones used in Gutsy?) Compiz update disabled the ability for "Magic Lamp" minimization effect to mimic the infamously "Genie Effect from Mac OSX" by limiting the "Magic Lamp Max Waves" from 0 to 3, for, probably patent issues. Some one has come with a solution to re-enable it by downloading source code, recompiling, risking breaking dependencies and such.

But there is a better/quicker way:

What you need: Compiz 0.5.5~git20070921+3v1ubuntu0 installed into your system, unsatisfied soul :guitar:,  gedit, ghex2

* You have to be root to modify the following files:

1. Use Hex editor to open "/usr/lib/compiz/libanimation.so"

2. Find "magic_lamp_max_waves", look for following "<min>3</min>", change "3" to "0"

3. Save, Close

4. Use Text Editor to open "/usr/share/compiz/animation.xml"

5. Find "magic_lamp_max_waves", look for following "<min>3</min>", change "3" to "0"

6. Save, Close

7. Restart GDM if the 3D desktop is currently running.

8. Set Minimization effect to "Magic Lamp", change Max Waves to "0"

Enjoy!

:lolflag:

*Without any major architectural changes to the Compiz effects, this patch will almost be guaranteed to work in any future versions. So if it breaks in next upgrade, fix it!

---

### Post by superyounan1 on 2007-10-19
Thanks a lot man, I was just about to post a new thread to complain about this. 

I'm gonna try it soon and come back to post the results

---

### Post by screaminj3sus on 2007-10-19
Nice, I missed that effect.

---

### Post by superyounan1 on 2007-10-19
dude it worked like a charm, thanks a lot.

I was using "sidekick" for minimizing instead because 3+ waves on magic lamp just looks goofy and cheap. I was getting used to sidekick, its not bad, but its nice to be back to what I'm used to.

Apple shouldn't be so finicky about random effects like that, Leopard took so many ideas from gnome and linux its not even funny. I like how they hailed their multiple desktop ideas as another amazing example of apple's creativity. Or how about that new "feature" of being able to scroll windows that aren't in focus? First its not a "feature", its just part of the system's behavior, and that too was just taken. On and on, everyone borrows from each other, if they're gonna get stingy about it, then they ought to stop swiping ideas themselves

---

### Post by jsully1 on 2007-10-19
Thanks so much, worked great for me as well!

---

### Post by Tex-Twil on 2007-10-21
Hi,
thanks for this help.
where can I set yhe last step i.e.

> Set Minimization effect to "Magic Lamp", change Max Waves to "0"

thanks

---

### Post by UMDGaara on 2007-10-21
It's in the Magic Lamp section under the Effects tab of the Animation plugin settings in the CompizConfig Settings Manager

CCSM should be in your System/Preferences menu. If it isn't, install it with:

```
$ sudo aptitude install compizconfig-settings-manager
```

If the shortcut isn't in your menu and you're sure it's installed, run it with the command:

```
$ ccsm &
```

Confirmed to work on Gusty as of 10/21/07 with the latest updates. Many thanks to FunkyRider for posting this. It's just what I was looking for!

---

### Post by Tex-Twil on 2007-10-22
> **UMDGaara said:**
> It's in the Magic Lamp section under the Effects tab of the Animation plugin settings in the CompizConfig Settings Manager

CCSM should be in your System/Preferences menu. If it isn't, install it with:

```
$ sudo aptitude install compizconfig-settings-manager
```

If the shortcut isn't in your menu and you're sure it's installed, run it with the command:

```
$ ccsm &
```

Confirmed to work on Gusty as of 10/21/07 with the latest updates. Many thanks to FunkyRider for posting this. It's just what I was looking for!

Ok, thank you. I've missed the "Effects" tab. Great ;)

---

### Post by sammydee on 2007-10-22
Wow thanks for the tip, I wasn't looking forward to having to recompile every time a new version of compiz came out just to get the nice minimise effect :)

I can't believe somebody granted apple a patent for a minimising animation!? All it does is create hassle for people that want to use alternative software.

sam

---

### Post by Tex-Twil on 2007-10-23
> **sammydee said:**
> 
I can't believe somebody granted apple a patent for a minimising animation!? All it does is create hassle for people that want to use alternative software.

sam

It's hard to believe for me too. What about eating apples, do we have to ask Apple first  for a permission ?

---

### Post by thespankguy on 2007-10-25
i'm using Hex Editor to navigate to libanimation.so, but i can't find "magic_lamp_max_waves". maybe i don't know exactly what i'm looking for? all i see are a bunch of seemingly random letters and numbers. the search function (at least what i think is a search function) won't let me type in anything

---

### Post by thespankguy on 2007-10-25
anyone?

---

### Post by jerkface27 on 2007-10-27
to funkyrider: thanks for the great post. this was driving me crazy for weeks.

to thespankguy: there should be two input fields on the search box. You want to type the phrase into the right side box. Click on it with your mouse and you should see a period (.) appear in the box. You should be able to start typing in to the box at this point.

---

### Post by th3gh05t on 2007-10-27
Hi,

How do I edit this file as root?

I tried sudo ghex /usr/lib/compiz/libanimation.so - but that didn't seem to work

A little help..

Oh, and how do you restart the GDM?

---

### Post by jerkface27 on 2007-10-27
th3gh05t: should be: sudo ghex2 /usr/lib/compiz/libanimation.so

I had that same problem; I was forgetting to put the 2 after ghex. To restart GDM, log out, then press ctrl-alt-backspace.

---

### Post by th3gh05t on 2007-10-29
Thanks jerkface! That worked!

Why don't you try and not be such a *jerk* next time!

---

### Post by limac on 2007-11-11
When trying to save it says "you don't have the permission to edit" and therefore I am unable to save it. so what should I do?

---

### Post by Tex-Twil on 2007-11-11
you must be root

---

### Post by JPMATRIX on 2007-11-20
So I followed every step but the effect just don't work (probably is my fault I am a complete noob)

See this please -->

[[IMG]http://img232.imageshack.us/img232/1754/screenshotyb2.th.png[/IMG]](http://img232.imageshack.us/my.php?image=screenshotyb2.png)

[[IMG]http://img249.imageshack.us/img249/9960/screenshot1ct4.th.png[/IMG]](http://img249.imageshack.us/my.php?image=screenshot1ct4.png)

Can you tell what am I doing wrong?

---

### Post by pun on 2007-11-25
> **JPMATRIX said:**
> So I followed every step but the effect just don't work (probably is my fault I am a complete noob)

See this please -->

[[IMG]http://img232.imageshack.us/img232/1754/screenshotyb2.th.png[/IMG]](http://img232.imageshack.us/my.php?image=screenshotyb2.png)

[[IMG]http://img249.imageshack.us/img249/9960/screenshot1ct4.th.png[/IMG]](http://img249.imageshack.us/my.php?image=screenshot1ct4.png)

Can you tell what am I doing wrong?


make sure your libanimation.so has <min>0</min>
not <min>0/min> it happen to me my first time 
when using ghex make sure you enable insert mode

---

### Post by JPMATRIX on 2007-11-26
thanks but problem solved :)

I forgot to add something in the "windows match"

(type=Normal | Dialog | ModalDialog | Utility | Unknown)

Still learning :P

---

### Post by lifeempowered.com on 2007-11-27
After following this, my "Animations" button disappeared in the Compiz Settings!  I reopened the libanimation file and my setting was saved and correct.  Any help is appreciated!

thanks

---

### Post by lifeempowered.com on 2007-11-27
Scratch that...got it working!

Thanks again for this thread!

---

### Post by gumbi18 on 2007-11-29
Brilliant thanks champ. Now I can enjoy compiz as it used to be...:)

---

### Post by PimpSquash on 2007-11-29
Worked excellent after, me, a noob tried to figure out how to use ghex2. I figured it out myself and I'm good. Now is there a way to make it go slow like on a Mac?

---

### Post by SirBlain on 2007-12-02
Okay so I did everything... set all the values to 0 with Hex and then Text editor... The first time I did it with compiz running and it crashed the app. Couldn't get it to start at all. So I reinstalled Compiz packages again and did it all over without compiz running. Same thing. 

Under the Visual Effects tab in the Appearance Preferences window if I click anything besides None... it kinda goes blank. Never really switches to Compiz. 

I really want the new effect but.. it would be nice to have compiz work too!

Oh and PimpSquash: Can't you just go to the Minimize Animation tab and double click Magic Lamp? Then just change the Duration Value to a higher number.

---

### Post by SirBlain on 2007-12-02
Lol... nvm. I'ma... bad word. I dunno if we're allowed to cuss but I don't wanna get kicked.

Anyway. I know I saw "just make sure you didn't erase part of the </min> code" But I didn't think it applied to me. Well. It did. Damnit.

But it's all good.

Now... if anyone could tell me how to slow it down like on a M... oh wait.

---

### Post by tekkenlord on 2007-12-11
The proposed solution for setting the max_waves to zero without the need for compilation is just brilliant. Thanks a lot!

---

### Post by El Chupacabras on 2007-12-14
I could have just hex edited the library!?!

I apt-got the source, changed animation.c and recompiled it!  ](*,)
I would have never figured out about the animations.xml, though. No wonder it wasn't working!

[[IMG]http://img141.imageshack.us/img141/5886/geniebt0.th.png[/IMG]](http://img141.imageshack.us/my.php?image=geniebt0.png)

---

### Post by thinch on 2008-03-10
Thanks, worked really well!  Just a little note though, instead of being root, you can also try

gksudo nautilus

in terminal, entering your password, and editing the files through that.  I didn't have the permissions to edit the files before, but this helped a lot.  Maybe its obvious to seasoned Ubuntu/Linux users, but it helped me.

A word of warning though.. This gives you complete control over all the files, even ones you shouldn't touch, so its worth closing the window I**MMEDIATELY** after any editing to avoid any problems.

---

### Post by soreau on 2008-04-14
Great contribution. Screw Macintosh for patenting a simple effect. What an easy hack. By the way, this worked for me with Gutsy's default compiz --version 0.6.3 Thanks a lot.

---

### Post by fahimdadream on 2008-04-29
Hey, so I followed what was said, except that now, when I click the animation button... none of my settings come up. It's just blank. Although the minimize settings I had still work. Any ideas?

---

### Post by slosd on 2008-05-10
Doesn't work for me. I use Ubuntu 8.04 and Compiz 0.7.4. 
I changed /usr/lib/compiz/libanimation.so:
[[IMG]http://img88.imageshack.us/img88/638/screenshot1hb1.th.png[/IMG]](http://img88.imageshack.us/my.php?image=screenshot1hb1.png)
but still I'm not able to set the option to 0:
[[IMG]http://img88.imageshack.us/img88/720/screenshot2jp8.th.png[/IMG]](http://img88.imageshack.us/my.php?image=screenshot2jp8.png)

---

### Post by fahimdadream on 2008-05-10
Hey, 

Did you change it in "/usr/share/compiz/animation.xml" also? 
You may have to restart your session as well, give that a shot, because it ended up working for me in the end, turns out I actually did the changes while I was RUNNING compiz... yes, not smart, I know. 

Just in case anyone cares, I reinstalled the plug-ins from synaptic, and then turned off all desktop effects, then did the changes and restarted the session, worked like a charm.

---

### Post by slosd on 2008-05-11
> **fahimdadream said:**
> Did you change it in "/usr/share/compiz/animation.xml" also? 

That's it! I didn't read the whole post and changed the value only in libanimation.so because I was so happy to see this is possible :D
It works now. Thanks.

---

### Post by toaste on 2008-05-16
Confirmed working in Hardy with the default Ubuntu build of Compiz (0.7.4).

A quick restart of x with ctrl-alt-backspace is sufficient to get everything reloaded properly.  Soul satisfied.


=D>

---

### Post by Can+~ on 2008-05-17
> **fahimdadream said:**
> Hey, so I followed what was said, except that now, when I click the animation button... none of my settings come up. It's just blank. Although the minimize settings I had still work. Any ideas?

I have that problem too.
edit: After reinstalling the main plugin package. I restarted all the steps, but with Compiz fusion turned off (replaced with metacity), and now it works. Apparently, I screwed it up when editing the hex on the first place.

---

### Post by anotherdisciple on 2008-05-17
Is there something like the streamline editor command that you can use with ghex2? any way to go to the terminal and perform a find/replace for "<min>3</min>"? because that would be awesome. I would like to write a script to do the ghex and the gedit command for you. I know how to do the gedit one... I just need help with the ghex one...

---

### Post by Ohwii on 2008-05-21
Hi, 

Could someone help It did exactly as in the guide but it does not work even with compiz off

help please.

---

### Post by Antilogo on 2008-06-23
It looks like no one else has had this problem, but when I go to activate animations in the CompizConfig Settings manager my emerald window decorator disappears, the avant window navigator won't open, and none of the other advanced effects work. Any suggestions?

---

### Post by Antilogo on 2008-06-23
Anybody? Help would be very much appreciated...

---

### Post by Can+~ on 2008-06-24
> **Antilogo said:**
> It looks like no one else has had this problem, but when I go to activate animations in the CompizConfig Settings manager my emerald window decorator disappears, the avant window navigator won't open, and none of the other advanced effects work. Any suggestions?

Did you made any other change to the binary file? (with ghex2). I accidentaly typed a character over the start of the file, saved without noticing, and everything exploded... But reinstalling the packages fixes it.

---

### Post by 1gor on 2008-06-25
i am unable to find ghex2 to install it, it isnt is synaptic, and when i download it it doesnt work what should i do.....?

---

### Post by saratchandra on 2008-06-26
I openeed the file using ghex, but I can't understand anything. Its all binary data.

---

### Post by saratchandra on 2008-06-26
Ok, I edited both files and compiz doesn't start properly. I can't see the title bar anymore. Disabled all animations right and everything is working properly.

---

### Post by Darin on 2008-06-27
The original instructions no longer work using Ubuntu 8.04 Hardy Heron, fully updated (security and recommended updates only) with Compiz 0.7.4 as of June 27, 2008. Using the original instructions, Compiz will either not start or disable the Animation plugin. The editing of one extra file is needed.

-----------------------------------------------------------

Here are new instructions:

If using Compiz currently, use Alt+F2 and Type: metacity --replace
Download ghex in Synaptic
Open a Terminal and Type:

1.) sudo ghex2 /usr/lib/compiz/libanimation.so

a.) Go to Edit->Find, click on the right hand box
b.) Type: magic_lamp_max and click find
c.) Change <min>3</min> from 3 to 0
d.) Save, Close

2.) sudo ghex2 /usr/lib/compiz/libanimation.a

a.) Go to Edit->Find, click on the right hand box
b.) Type: magic_lamp_max and click find
c.) Change <min>3</min> from 3 to 0
d.) Save, Close


3.) sudo gedit /usr/share/compiz/animation.xml

a.) Go to Search->Find
b.) Type: magic_lamp_max and click find, scroll down past the languages
c.) Change <min>3</min> from 3 to 0
d.) Save, Close

Restart, log out and back in, or Alt+F2 and Type: Compiz --replace. Any of these should work. Use CompizConfig to change the Magic Lamp Settings.

-----------------------------------------------------------

Hopefully these instructions work. Thanks to the original poster for the original instructions!

- Darin

---

