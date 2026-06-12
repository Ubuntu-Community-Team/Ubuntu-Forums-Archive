---
title: "The best way to install Compiz Fusion on Ubuntu Feisty"
date: 2007-08-27
forum: Desktop Effects &amp; Customization
---

### Post by Forlong on 2007-08-27
I have written a complete how-to over the weekend how you can install and configure the packages of Amaranth's repository:
[The best way to install Compiz Fusion on Ubuntu Feisty](http://forlong.blogage.de/article/2007/8/26/The-best-way-to-install-Compiz-Fusion-on-Ubuntu-Feisty)

--------------------------------------------------
[COLOR="Red"]_Update:_[/COLOR] I finally managed to put up another how-to that's recommended for Kubuntu and Xubuntu users. Just follow the link above and decide after the introduction which guide to use.
--------------------------------------------------

These packages have been backported from Gutsy (Ubuntu's next release) and are therefore pretty stable in comparison to the other packages around.

I took the time to write this because I felt it was necessary to give people that are new to Ubuntu and/or Compiz a detailed guide how to set things up (more experienced users can use this as well, of course).
Also there are a lot of threads in the forums with people complaining latest update broke their Compiz, or the like.
I think this is mostly due to the fact, that the packported repository isn't established enough - most people seem not to know there's a reasonable alternative to a bleeding edge install.

I hope this will help people to get an awesome Compiz Fusion install as well as a glimpse of how to set things up.


Regards,
Nick


P.S. The guide is written with the "standard ubuntu user" in mind - that means it focuses on installing Compiz Fusion on GNOME.
I'm writing an additional guide for experienced users atm (exclusively with terminal  commands), where I will also focus on installing Compiz Fusion on KDE and Xfce.

---

### Post by ru0n on 2007-08-27
Great Guide! I'll try it out later today.
;)

---

### Post by CAD-MAN on 2007-08-27
Ah, good stuff - I'll give it a try in a couple of days! :)

---

### Post by Pablo Pablovski on 2007-08-27
Thanks - really useful guide to setting up Compiz. I've bookmarked it for when things go sadly awry. :)

---

### Post by BottomsUp on 2007-08-27
Awesome thanks. Yes, Im new to Linux and yes Ive been stuggling with this for days.

I ran into a problem. When I get to the part about launching Compiz under First steps I cant launch it.

The problem is this button were there from a previous failed attempt and didnt disappear after I removed the package. Clicking it does nothing. I also have a compiz icon in another location. See screeshots below...any ideas?

TIA

[[IMG]http://img167.imageshack.us/img167/1600/84651534ym7.png[/IMG]](https://addons.mozilla.org/firefox/1174)
[[IMG]http://img167.imageshack.us/img167/2220/85405542qc5.png[/IMG]](https://addons.mozilla.org/firefox/1174)

---

### Post by Forlong on 2007-08-27
The fusion-icon is not included in the repository, as it's not considered to be stable enough.

But you don't really need that anyway. Just do as I said in the how-to:
Press [Alt]+[F2] and type:
```
compiz --replace
```

If you want a starter on the panel (or the desktop) use this command for that - also if you want to start Compiz by default, add this command to **System &#8594; Preferences &#8594; Sessions &#8594; Startup Programs**.

I hope this helps.

The Compizconfig Settings Manager icon should work, though.


P.S. if there's a specific part in the guide that's not clear enough for you or if you miss something, please leave a comment in the blog entry, so I can advance the how-to.

---

### Post by orange2k on 2007-08-27
I followed this guide, and let me tell you: this is the best ******* guide for installing compiz fusion that Ive seen so far. For the first time since I started using compiz (or beryl for that matter), can I say that Ive experienced no troubles or errors. No more constant searching and asking unneccessary questions on the forum for me...

I think this guide of yours deserves a special place in the forum, as the best/most-easy-to-use for newbies such as myself...

It should become a sticky...

One more time: this kicks major ***...:)

---

### Post by ozzyprv on 2007-08-27
thank you Forlong.

I will give it a try once I get home.
I have try every single guide out there for installing Compiz. So far, no luck.
This is what always happens:
I always start from strach, clean install followed by a Nvidia driver update to get my 1140x900 resolution.
Then as soon as I enable Desktop Effects I loss my wondow borders. The only way to get them back is by running "metacity --replace" which in turn stops Compiz....

Forlong, does your guide assumes one has "Desktop Effects" enabled? 

Thank you.

---

### Post by BottomsUp on 2007-08-27
> **Forlong said:**
> The fusion-icon is not included in the repository, as it's not considered to be stable enough.

But you don't really need that anyway. Just do as I said in the how-to:
Press [Alt]+[F2] and type:
```
compiz --replace
```

If you want a starter on the panel (or the desktop) use this command for that - also if you want to start Compiz by default, add this command to **System &#8594; Preferences &#8594; Sessions &#8594; Startup Programs**.

I hope this helps.

The Compizconfig Settings Manager icon should work, though.


P.S. if there's a specific part in the guide that's not clear enough for you or if you miss something, please leave a comment in the blog entry, so I can advance the how-to.

Thanks. My problem is that when I try to perform this step..clicking the CompizConfig Settings Manager via System &#8594; Preferences doesn´t do anything. Its like the button is corrupted or something. Any ideas? 

Also, if I run compiz --replace from the terminal I get this message. **compiz (core) - Fatal: No composite extension**. I ran it from Alt-F2, but nothing happened.
Thanks again.

[I]First steps

Before we launch Compiz for the first time, start the CompizConfig Settings Manager via System &#8594; Preferences.

    * There we click on Preferences and in the Backend section choose "Flat-file Configuration Backend" (this is the most reliable and it won't mess with your previous settings of Compiz in gconf).
    * Then click Back and look for the Window Decoration button. Right next to Command, type gtk-window-manager (this will prevent the window borders to disappear in certain situations) - if you want to use Emerald as your default window decorator, see below.
[/I]

---

### Post by Techpenguin on 2007-08-27
when i finally manage to get ubuntu i'll try it

---

### Post by Forlong on 2007-08-27
> **ozzyprv said:**
> as soon as I enable Desktop Effects I loss my wondow borders.
The guide should cover this problem. If not, please let me know.
> **ozzyprv said:**
> Forlong, does your guide assumes one has "Desktop Effects" enabled?
No, in fact you should disable desktop effects prior installing and remove them (just like I describe in the how-to).
> **BottomsUp said:**
> if I run compiz --replace from the terminal I get this message. **compiz (core) - Fatal: No composite extension**
That depends on your type of graphics card and what driver you are using. For example, if you are using an ATI card with the fglrx driver, you will need to set up [Xgl](https://help.ubuntu.com/community/CompositeManager/Xgl).

I'm sorry, but I can't cover every individual problem with setting up the premises for desktop effects in a single how-to. But don't hesitate to ask again, I'll see what I can do.


@orange2k: thank you very much for your kind words (and the not so kind ones, lol). That makes the whole work I put into it worthwhile.
So don't hesitate to post such commands to the entry as well ^^

---

### Post by boiiinnnnnnnnnnnnnnnnggg on 2007-08-27
I tried this tutorial after another ( [http://kevin.vanzonneveld.net/techblog/article/enable_compizfusion_in_ubuntu_feisty/](http://kevin.vanzonneveld.net/techblog/article/enable_compizfusion_in_ubuntu_feisty/) ) failed me. I removed everything related to compiz/beryl/emerald prior to doing this as the tutorial suggested, and it has gotten me farther than any other tutorial has. 

However, it still doesn't work. When I use the standard GConf config. backend, the titlebars disappear and when I use Flat file, my computer freezes completely (not even alt+ctrl+backspace works).

I am using an Intel Core 2 Duo 64-bit, and an NVidia GeForce Go 7400. I don't know what the problem could be - the only suspicion I have is that it might have something to do with the NVidia drivers that were installed by Envy from using [this]("http://kevin.vanzonneveld.net/techblog/article/enable_compizfusion_in_ubuntu_feisty/") tutorial.

Does anyone have a solution?

---

### Post by BottomsUp on 2007-08-27
> **Forlong said:**
> The guide should cover this problem. If not, please let me know.

No, in fact you should disable desktop effects prior installing and remove them (just like I describe in the how-to).

That depends on your type of graphics card and what driver you are using. For example, if you are using an ATI card with the fglrx driver, you will need to set up [Xgl](https://help.ubuntu.com/community/CompositeManager/Xgl).

I'm sorry, but I can't cover every individual problem with setting up the premises for desktop effects in a single how-to. But don't hesitate to ask again, I'll see what I can do.


@orange2k: thank you very much for your kind words (and the not so kind ones, lol). That makes the whole work I put into it worthwhile.
So don't hesitate to post such commands to the entry as well ^^

No worries. Thanks a ton for your help. Let me read up on XGL and I'll be back :-)

---

### Post by ozzyprv on 2007-08-27
> **Forlong said:**
> The guide should cover this problem. If not, please let me know.

Ok. The addition of gtk-window-decorator (over other guides I followed before) prevent the borders from disappearing. But the main issue, the loss of the control over the windows remains.
I have the the window borders, I can maximize and minimize, but I cannot move the windows around (drag). 
[COLOR="RoyalBlue"]EDIT1 : The default windows switcher does not work either.
EDIT2: After doing some more reading, it seems like by enabling Compiz, I somehow loss the "window manager" capabilities. I recover the ability to move (drag) and switch between windows when I do: "metacity --replace".[/COLOR]
[COLOR="Red"]EDIT3: Window manager problem FIXED. I am sorry Forlong, as far as I can tell, it was nothing to do with your guide.
I was spoiled by Metacity controlling everything for me. When Compiz takes over the window manager activities, you have to specify every bit and piece of the windows managing. For example: movements, not-loading-windows-out-of-focus, etc. All done via the "Window Manager plug-ins.[/COLOR]

---

### Post by ozzyprv on 2007-08-27
> **boiiinnnnnnnnnnnnnnnnggg said:**
> ..... the only suspicion I have is that it might have something to do with the NVidia drivers that were installed by Envy from using [this]("http://kevin.vanzonneveld.net/techblog/article/enable_compizfusion_in_ubuntu_feisty/") tutorial.

Does anyone have a solution?

I update my Nvidia drivers by running "get-apt install nvidia-glx-new" instead. My computer does not freeze when using the flat-file backend. 

Try using[ this HOW-TO ]("http://ubuntuforums.org/showthread.php?t=432056")to update your Nvidia driver. Please post if it works (or not).

---

### Post by KCPokes on 2007-08-27
Just wanted to say THANKS!  I've had my challenges with different managers, but followed your guide, to the T, and everything worked flawlessly.

---

### Post by ozzyprv on 2007-08-28
After finally  getting into Ubuntu/Linux full mode,  I spent the last week or so trying to install both the latest version of my Nvidia card driver AND Compiz-Fusion.
Well as I said, a week or so. Until today.

Thank you Forlong for this guide. It should be within the Sticky Threads!

---

### Post by boiiinnnnnnnnnnnnnnnnggg on 2007-08-28
> **ozzyprv said:**
> I update my Nvidia drivers by running "get-apt install nvidia-glx-new" instead. My computer does not freeze when using the flat-file backend. 

Try using[ this HOW-TO ]("http://ubuntuforums.org/showthread.php?t=432056")to update your Nvidia driver. Please post if it works (or not).

I used "sudo apt-get install nvidia-glx-new". Compiz now works with the flat-file backend, however, the title bar error still persists.

---

### Post by ozzyprv on 2007-08-28
> **boiiinnnnnnnnnnnnnnnnggg said:**
> I used "sudo apt-get install nvidia-glx-new". Compiz now works with the flat-file backend, however, the title bar error still persists.

Tell me about that error, after a week trying to fix this I may be able to help you.

---

### Post by Forlong on 2007-08-28
Regarding the window boarder problem with nvidia:

Try adding these options to your xorg.conf.
You need to be root to modify that file:
```
sudo gedit /etc/X11/xorg.conf
```
Look for the **Section "Device"** and add
```
Option      "AddARGBGLXVisuals" "true"
```
You should also make sure your **DefaultDepth** (in *Section "Screen"*) is set to **24**

I'm not a nvidia user, though... so I can't test whether it should work or not.

---

### Post by sway.jd on 2007-08-28
is it just me or the link is down?

---

### Post by Forlong on 2007-08-28
Sorry, I noticed that too.
I guess the guys over at blogage.de are updating the software again (it's beta).

Sorry for the inconvenience. It's [back on](http://forlong.blogage.de/).

---

### Post by sway.jd on 2007-08-28
cool! i'll give it a try.

will post the results shortly.

---

### Post by sway.jd on 2007-08-28
worked great.

I haven't rebooted yet. the compiz --replace in the start up progrmas hasn't work with the previous isntallations though, so I guess its not working yet.

so is there a way to add an icon that starts the compiz? that would be great.


also, I could never find how to get my favourite minimise (and maximise) animation working since it has evolved from beryl.

is the one you see in this video: [http://www.youtube.com/watch?v=ZD7QraljRfM](http://www.youtube.com/watch?v=ZD7QraljRfM) (second 45)


thanks alot for the guide!

---

### Post by ArtF10 on 2007-08-28
Will I be able to do follow this on Fluxbuntu?

---

### Post by Hyperkill on 2007-08-28
Thank you so much!  I finally have compiz running good after days of working on it and using useless download/install scripts.  If you weren't a man, I'd kiss you!

---

### Post by Goodson1974 on 2007-08-28
Hi Forlong

Superb guide mate, i've finally got some superb Compiz Fusion action going now!

I'm having one problem.  When i add compiz --replace to the startup bit of sessions, it has disappeared the next time i start up my PC so i have to start Compiz manually.  Any ideas why this might be happening?

Cheers dude.

---

### Post by Forlong on 2007-08-28
> **sway.jd said:**
> I haven't rebooted yet. the compiz --replace in the sI haven'tart up progrmas hasn't work with the previous isntallations though, so I guess its not working yet.
I don't know why it wouldn't work for you. I'll keep my fingers crossed. :)
> **sway.jd said:**
> so is there a way to add an icon that starts the compiz? that would be great.
Certainly. All you have to do is *right-cklick on your panel &#8594; Add to panel &#8594; Custom Application Launcher* and use *compiz --replace* as the command.
(or you right-click on your desktop and choose *Create Launcher*)
> **sway.jd said:**
> also, I could never find how to get my favourite minimise (and maximise) animation working since it has evolved from beryl.
Believe it or not... this feature had to be removed due to the fact that Apple has a patent on that. 
> **ArtF10 said:**
> Will I be able to do follow this on Fluxbuntu?
That's a tricky question and it requires a lot of information.
If I had to answer the question right away, I'd say no.
That's because Fluxbuntu is based on Dapper and these are Feisty packages.
Theoretically you can upgrade your Fluxbuntu to Feisty - but I wouldn't recommend it.
Last but not least: Compiz is a window manager - as is fluxbox. So you can't run both at a time. That pretty much makes the whole fluxbuntu install pointless ;)
> **Goodson1974 said:**
> When i add compiz --replace to the startup bit of sessions, it has disappeared the next time i start up my PC so i have to start Compiz manually.
Does the entry really disappear or do you mean Compiz won't run, although it's included in *Startup Programs*?
Do you have any additional programs, that you added there yourself?


P.S. thanks again for all the nice comments. I really appreciate it.

---

### Post by Goodson1974 on 2007-08-28
Thanks for the quick reply!

The entry does disappear.  I haven't added any programs to the startup before.

---

### Post by mzmiric5 on 2007-08-28
This is the best guide i could fine on this forums, thanx m8, i was trying to setup cf on my ubuntu for days i wiped my disk 11 times. After this tutorial i got it working. But i have noticed that my mouse and keyboard just stop working, and ubuntu freezes. Btw does any1 know how to enabel sli on 2x8600s GT. once again tnx a lot m8 this guide is really to kill for.

---

### Post by ArtF10 on 2007-08-28
I have a question regarding the first step..I've done a clean Ubuntu Fiesty Fawn install and have not gone anywhere near desktop effects/compiz.  Do I still need to go through Synaptic and remove Compiz.....there shouldn't be anything there really.

Couldn't I just go like this and remove desktop-effects:
```

sudo apt-get remove compiz-core desktop-effects 
sudo apt-get remove compiz compiz-gnome 
sudo apt-get remove compizconfig-settings-manager 
sudo apt-get remove compiz-fusion-plugins-extra
sudo apt-get remove compiz-fusion-plugins-unofficial 
sudo apt-get remove libcompizconfig-backend-gconf
```
> **Forlong said:**
> ...That's a tricky question and it requires a lot of information.
If I had to answer the question right away, I'd say no.
That's because Fluxbuntu is based on Dapper and these are Feisty packages.
Theoretically you can upgrade your Fluxbuntu to Feisty - but I wouldn't recommend it.
Last but not least: Compiz is a window manager - as is fluxbox. So you can't run both at a time. That pretty much makes the whole fluxbuntu install pointless ;)...

ok, that's fine,,,,what about installing it on XUbuntu?  Would that work?

---

### Post by sway.jd on 2007-08-28
> **Forlong said:**
> I don't know why it wouldn't work for you. I'll keep my fingers crossed. :)

worked this time mate. must be because you crossed them cause I can't think of another explanation.

> Certainly. All you have to do is *right-cklick on your panel &#8594; Add to panel &#8594; Custom Application Launcher* and use *compiz --replace* as the command.
(or you right-click on your desktop and choose *Create Launcher*)


ah... thanks! I'm sure it will be useful.

> Believe it or not... this feature had to be removed due to the fact that Apple has a patent on that. 

Damn! was the nicer. i'm really sad now.

but wait. are you sure? cause the 1st time I installed compiz fusion it came with that one by default. but due to some problems I uninstalled it and when i installed it again (still with problems) i had magical lamp by default and never new why.

is it possible that it was removed by the time I installed it the second time?



Anyway, big thanks for the answers!

---

### Post by Forlong on 2007-08-28
> **Goodson1974 said:**
> The entry does disappear.  I haven't added any programs to the startup before.
Hm... that's pretty weird - are you sure you set it correctly?
Please post the output of
```
ls ~/.config/autostart
```
> **ArtF10 said:**
> I have a question regarding the first step..I've done a clean Ubuntu Fiesty Fawn install and have not gone anywhere near desktop effects/compiz.  Do I still need to go through Synaptic and remove Compiz.....there shouldn't be anything there really.
Desktop effects is nothing else than a modified version of Compiz (well, in fact it's not even really modified). So, yes - you do have to remove all the packages you'll find, when doing a search for *compiz* in Synaptic.
If you want to use the terminal, this will also do the job:
```
sudo apt-get remove compiz* && sudo apt-get autoremove
```
> **Goodson1974 said:**
> what about installing it on XUbuntu?  Would that work?
It will work but I wouldn't recommend it, since it will pull lots of GNOME-dependencies.
I'm working on an alternative guide for Kubuntu and Xubuntu users, that will solely focus on terminal commands and tells you which packages to install.
In fact I did finish it this minute - but I'm too tired right now to publish it. This is my first blog and I have to get used to the limited space. Setting up the first guide was a royal pain in the ***, because you have to make up some workarounds in order to keep a decent layout.

I promise this will be up tomorrow.
> **sway.jd said:**
> worked this time mate. must be because you crossed them cause I can't think of another explanation.
You're welcome ^^
> **sway.jd said:**
> but wait. are you sure? cause the 1st time I installed compiz fusion it came with that one by default. but due to some problems I uninstalled it and when i installed it again (still with problems) i had magical lamp by default and never new why.

is it possible that it was removed by the time I installed it the second time?
No, you're right. I assume you used Treviños repository - he patched the magic lamp animation so you can set it's waves to 0. Ubuntu could never distribute such a patch but maybe Trev will publish his sometime.

---

### Post by ArtF10 on 2007-08-28
> **Forlong said:**
> .....
I'm working on an alternative guide for Kubuntu and Xubuntu users, that will solely focus on terminal commands and tells you which packages to install.
In fact I did finish it this minute - but I'm too tired right now to publish it. This is my first blog and I have to get used to the limited space. Setting up the first guide was a royal pain in the ***, because you have to make up some workarounds in order to keep a decent layout.

I promise this will be up tomorrow........


You are really making it enticing now...I'll hardly be able to sleep.  I think I'll wait for tomorrow and try it on XUbuntu. 

I'm sure that I am not alone, among XUbuntu users, in thanking you for making this attempt at providing something for us.

---

### Post by jbman on 2007-08-28
followed the blog tested working great, many thanks very easy to follow

---

### Post by Bart_D on 2007-08-28
> **Forlong said:**
> ....Desktop effects is nothing else than a modified version of Compiz (well, in fact it's not even really modified). So, yes - you do have to remove all the packages you'll find, when doing a search for *compiz* in Synaptic.
If you want to use the terminal, this will also do the job:
```
sudo apt-get remove compiz* && sudo apt-get autoremove
```
...

If I use the terminal code, will I be able to go straight to Settings>Repositories and then follow the instructions from there?

---

### Post by cudaman73 on 2007-08-29
I'm having the same problem that another guy was back on the third page.

I did manage to get everything to run fine (couldn't get the settings manager to run properly, but it turned out i totally skipped the initial removal of desktop-effects) up until i ran compiz --replace. it acts like it normally does, but then i lose any windows open, and the system totally hardlocks. the only way to fix it is to reboot.

Did I miss something?

---

### Post by Copyright on 2007-08-29
Hey,

I've done all the steps in order (multiple times) however when I go to do either

A) compiz --replace

I get this error (I ran it from the terminal to get this info)

xxxxx@xxxxx:~$ compiz --replace
Checking for Xgl: not present. 
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: not present. 
aborting and using fallback: /usr/bin/metacity 

B) emerald --replace

(emerald:6777): GLib-GObject-CRITICAL **: g_object_ref: assertion `G_IS_OBJECT (object)' failed


I have followed the guide to what I can see perfectly, little baffled by whats causing it :(

Cheers,
Copyright

---

### Post by cudaman73 on 2007-08-29
> **Copyright said:**
> Hey,

I've done all the steps in order (multiple times) however when I go to do either

A) compiz --replace

I get this error (I ran it from the terminal to get this info)

xxxxx@xxxxx:~$ compiz --replace
Checking for Xgl: not present. 
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: not present. 
aborting and using fallback: /usr/bin/metacity 


It appears that you don't have Xgl installed or configured, and thus, you have no composite extension with which to run compiz.

I'm presuming you have an ATI video card. Either way, however, you need to get the proper drivers installed before you can run compiz, as the proper drivers allow the composite extension to run properly (or at all). There are plenty of links in the Hardware/Laptop sub-forum on how to get Xgl working.

---

### Post by Copyright on 2007-08-29
> **cudaman73 said:**
> It appears that you don't have Xgl installed or configured, and thus, you have no composite extension with which to run compiz.

I'm presuming you have an ATI video card. Either way, however, you need to get the proper drivers installed before you can run compiz, as the proper drivers allow the composite extension to run properly (or at all). There are plenty of links in the Hardware/Laptop sub-forum on how to get Xgl working.

Actually its an Nvidia Geforce GO7600, I have the latest drivers installed though I'll go read now how to get Xgl working.

Thanks mate!

---

### Post by cudaman73 on 2007-08-29
> **Copyright said:**
> Actually its an Nvidia Geforce GO7600, I have the latest drivers installed though I'll go read now how to get Xgl working.

Thanks mate!

In that case, make sure that your /etc/X11/xorg.conf has the Option "Composite" "Enable" in the Extensions section. If you add that line, you will have to restart your X session (ctrl-alt-backspace should do it), and that should work.

---

### Post by Copyright on 2007-08-29
Thanks heaps for the help, followed a XGL guide and its running like a charm except like someone else I lost the windows borders, I tried this listed below to no avail.



> **Forlong said:**
> Regarding the window boarder problem with nvidia:

Try adding these options to your xorg.conf.
You need to be root to modify that file:
```
sudo gedit /etc/X11/xorg.conf
```
Look for the **Section "Device"** and add
```
Option      "TripleBuffer"      "true"
Option      "AddARGBGLXVisuals" "true"
```
You should also make sure your **DefaultDepth** (in *Section "Screen"*) is set to **24**

I'm not a nvidia user, though... so I can't test whether it should work or not.

---

### Post by cudaman73 on 2007-08-29
> **Copyright said:**
> Thanks heaps for the help, followed a XGL guide and its running like a charm except like someone else I lost the windows borders, I tried this listed below to no avail.

Did you try setting the command in "Window Decorations" to "gtk-window-manager"?

alternatively, i believe you can run "emerald --replace" after running "compiz --replace" to acheive the same end.

Perhaps I need to get XGL working in order to stop my system from locking up.

I'll give it a try.

I suppose I should give you thanks :P

---

### Post by Copyright on 2007-08-29
the output from trying to run compiz is

/usr/bin/compiz.real (core) - Error: Can't load plugin 'ccp' because it is built for ABI version 20070708 and actual version is 20070828
/usr/bin/compiz.real (core) - Error: Couldn't activate plugin 'ccp'

---

### Post by cudaman73 on 2007-08-29
> **Copyright said:**
> the output from trying to run compiz is

/usr/bin/compiz.real (core) - Error: Can't load plugin 'ccp' because it is built for ABI version 20070708 and actual version is 20070828
/usr/bin/compiz.real (core) - Error: Couldn't activate plugin 'ccp'

I had the same error at one point. I've installed compiz at least six times in the past three hours, and i keep getting either no titlebars, or a total hardlock (except for mouse input).

I have no idea what that means, other than apparently the ABI version has to be the same as the one in the 'ccp' plugin. heh :P

---

### Post by Copyright on 2007-08-29
> **cudaman73 said:**
> I had the same error at one point. I've installed compiz at least six times in the past three hours, and i keep getting either no titlebars, or a total hardlock (except for mouse input).

I have no idea what that means, other than apparently the ABI version has to be the same as the one in the 'ccp' plugin. heh :P

Yup I got EXACTLY the same in both losing titlebars and the mouselock.  Looks like we both are in the same boat :P

---

### Post by cevil203 on 2007-08-29
mm i installed compiz fusion today. i was able to get in running earlier, by typing compiz --replace at boot, then typing compiz -replace to get borders back. unfortunately i just followed those instructions on a post 


Quote:
Originally Posted by Forlong View Post
Regarding the window boarder problem with nvidia:

Try adding these options to your xorg.conf.
You need to be root to modify that file:
Code:

sudo gedit /etc/X11/xorg.conf

Look for the Section "Device" and add
Code:

Option      "TripleBuffer"      "true"
Option      "AddARGBGLXVisuals" "true"

You should also make sure your DefaultDepth (in Section "Screen") is set to 24

I'm not a nvidia user, though... so I can't test whether it should work or not.

and it made things worse. i can no longer see my terminal because it is just pure white...great haha.  that command to bring back the title bar doesnt work for me. hopefully sum genius here can figure it out :D

---

### Post by cudaman73 on 2007-08-29
> # Then click Back and look for the Window Decoration button. Right next to Command, type gtk-window-manager (this will prevent the window borders to disappear in certain situations) - if you want to use Emerald as your default window decorator, see below.

did you try this part of the guide? It didn't work for me, but you never answered when i asked it earlier. Supposedly that is one way to fix the titlebars disappearing.

---

### Post by cevil203 on 2007-08-29
i used this guys method btw  (still no titlebar) and i have noe idea what your talking about when you say "window decoration"

[http://ubuntu4life.blogspot.com/2007/07/lets-get-started.html](http://ubuntu4life.blogspot.com/2007/07/lets-get-started.html)

---

### Post by cudaman73 on 2007-08-29
> **cevil203 said:**
> i used this guys method btw  (still no titlebar) and i have noe idea what your talking about when you say "window decoration"

[http://ubuntu4life.blogspot.com/2007/07/lets-get-started.html](http://ubuntu4life.blogspot.com/2007/07/lets-get-started.html)

That guy appears to be linking to Trevino's repo and using the latest compilation from git.

That's not always guaranteed to work (like anything related to compiz ever is -_-).

in "Compizconfiguration-settings-manager" (type ccsm in your terminal), you set up what compiz plugins you want enabled. Look for Window Decorations, and in the command part, type 'gtk-window-manager'.

---

### Post by cevil203 on 2007-08-29
ah  i did this but nothing seems to happen

---

### Post by cudaman73 on 2007-08-29
Yeah, I've given up on compiz for now.

I'm tired, and I have to get up in less than five hours for class.

I'll be back and trying again once I get out.

---

### Post by cevil203 on 2007-08-29
yaa tommorow is another day. i just wanna get it workin before i move back to school

---

### Post by Forlong on 2007-08-29
> **Bart_D said:**
> If I use the terminal code, will I be able to go straight to Settings>Repositories and then follow the instructions from there?
Yes, but I really don't know why you shouldn't just follow the instructions as you have Synaptic already running...
> **cudaman73 said:**
> up until i ran compiz --replace. it acts like it normally does, but then i lose any windows open, and the system totally hardlocks.
Did you switch to Flat-file backend? If you already used Compiz before there might be some interference with previous settings.

Can you post the output of *compiz --replace* in a terminal?
> **Copyright]/usr/bin/compiz.real (core) - Error: Can't load plugin 'ccp' because it is built for ABI version 20070708 and actual version is 20070828[/QUOTE]
Did you really remove all packages related to Compiz and more importantly, did you remove all other third-party repositories regarding Compiz/Beryl before adding the one from the how-to?!
(I have to add this to the guide)
[QUOTE=cevil203 said:**
> unfortunately i just followed those instructions on a post 
[...]
and it made things worse. i can no longer see my terminal because it is just pure white...great haha.
Then please remove it again.


To everyone having problems with their titlebars on nvidia, try this:
```
sudo nvidia-xconfig --add-argb-glx-visuals -d 24
```
This should add the proper commands automatically to your xorg.conf

Then press [Ctrl]+[Alt]+[Backspace] to restart your XServer.

Please let me know if this works for you.

---

### Post by Ascension on 2007-08-29
Wow I like this. Very nice.

---

### Post by orange2k on 2007-08-29
Everything works perfectly for me - the best part is that I turned off the repository that I used to install compiz fusion from, so I have a perfectly stable version that doesnt update itself possibly causing problems...

Great, fantastic guide!!! :)

---

### Post by Forlong on 2007-08-29
> **Ascension said:**
> It downloaded 15 files is that how many it usually downloads?
That obviously depends on how many packages you chose to install.
**compiz** alone will pull (at least) 9 packages and **compizconfig-settings-manager** another 3. That already makes 12 and if you picked emerald, it will be another 2 and with **emerald-themes** or **sexy-python** that's... um... you do the math. :)


@orange2k: thanks again, I'm glad that it works great for you.

---

### Post by Ascension on 2007-08-29
Wow, didnt know there were so many things you could do to it, or any operating system. Totally new to Ubuntu, got it yesterday.

---

### Post by cudaman73 on 2007-08-29
> **Forlong said:**
> Did you switch to Flat-file backend? If you already used Compiz before there might be some interference with previous settings.

ccsm already had the flat-file backend selected when i ran it. I've tried other guides since this one, so i'll have to remove all traces of compiz and try again fresh to give you the output of compiz --replace.

Will edit when I have the info.

---

### Post by Forlong on 2007-08-29
> **cudaman73 said:**
> ccsm already had the flat-file backend selected when i ran it.
Then create a new profile in **Preferences**.
(I suggest that in the configuring section of the how-to - going to move it to the first steps)

---

### Post by cudaman73 on 2007-08-29
well, after removing all the config files related to compiz (including one or two i had missed), the system still hardlocks. However, I managed to get cat to write the output of the program to a file.

```
m3r1k@reborn-laptop:~$ cat compizlog 
Checking for Xgl: not present. 
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
Checking for nVidia: present. 
Checking for Xgl: not present. 

```

I'm presuming it hardlocks after checking for XGL again.

---

### Post by Copyright on 2007-08-29
I ended up messing around for a few hours and after many things, I got the little fella running.  All I can say is its awsome!

The only issue I have now is my opengl windows are transparent and the fix of going into compiz settings and deleted the 'unknown' setting from the opacity settings doesnt work since my computer has no 'unknown' setting, apart from that its awsome.

---

### Post by cudaman73 on 2007-08-29
> **Copyright said:**
> I ended up messing around for a few hours and after many things, I got the little fella running.  All I can say is its awsome!

The only issue I have now is my opengl windows are transparent and the fix of going into compiz settings and deleted the 'unknown' setting from the opacity settings doesnt work since my computer has no 'unknown' setting, apart from that its awsome.

I'm glad you got it working! :grin:

Now to get mine to do the same.

---

### Post by cudaman73 on 2007-08-29
Update:

I GOT IT TO WORK!

Yes. *dances*

Thank you everyone for your help.

---

### Post by Bart_D on 2007-08-29
[QUOTE=Forlong;3272679]Yes, but I really don't know why you shouldn't just follow the instructions as you have Synaptic already running.../QUOTE]

No no, I intend on going through Synaptic, but its just that this way seems quicker.  I would have never thoughtabout it but since the question was asked, I thought about it.

Thanks fort he reply.

---

### Post by Forlong on 2007-08-29
> **Copyright said:**
> The only issue I have now is my opengl windows are transparent
Try **CCSM &#8594; Workarouns &#8594; Legacy Fullscreen Support**

If this doesn't work, go to  **CCSM &#8594; General Options &#8594; Opacity Settings**, click on **Add** and type
```
name=<name of the application>
``` and set it to **100**
> **cudaman73 said:**
> I GOT IT TO WORK!
Great. :)
Do you know what has been the problem?
> **Bart_D said:**
> No no, I intend on going through Synaptic, but its just that this way seems quicker.
I see. Just click on the button in the up left corner (above all the check boxes). This will list all installed packages first.
Then click on the first entry (not the check box), hold [Shift] and click on the last one installed. Then mark for removal.

---

### Post by cudaman73 on 2007-08-29
> **Forlong said:**
> 
Great. :)
Do you know what has been the problem?

I believe it was a package that needed to be uninstalled from my fresh install of ubuntu. One that I had missed several times.
At any rate, it works now.

Is there a fuzion-icon deb for amd64?

---

### Post by Forlong on 2007-08-29
Finally, the alternative How-To is up!
This focuses on the terminal and is **recommended for Kubuntu and Xubuntu users**.

Please continue to visit the [original entry]("http://forlong.blogage.de/article/2007/8/26/The-best-way-to-install-Compiz-Fusion-on-Ubuntu-Feisty") and decide after the introduction which guide to use.

Because of that, I had to move the section about setting up Compiz Fusion to a [separate guide]("http://forlong.blogage.de/article/2007/8/29/How-to-set-up-Compiz-Fusion").


I hope you like it.

Regards,
Nick

---

### Post by Goodson1974 on 2007-08-29
Hi Forlong

This is what I get when I enter ls ~/.config/autostart in the terminal

mat@mat-desktop:~$ ls ~/.config/autostart
beagled.desktop

---

### Post by quattroman on 2007-08-29
I got some trouble with compiz + firefox. I get a white borther around it covering the title bar and the close, max, min buttons.

please look at the pic for more reference.

Thanks

---

### Post by stillious on 2007-08-29
Hi,

Great guide (got me further than any other out there) :) I Have the problem of missing title bar & menu bar.

In CompizConfig Settings Manager:

1) I have set Window Decoration -> Command to "gtk-window-manager" (If removed, no difference)
2) Prefs -> Backend is set to "Flat-file Configuration Backend" (no difference with GConf Config)

Here is a section of my xorg.conf: [ATTACH]42049[/ATTACH]

n.b I use an Nvidia graphics card with the latest drivers installed.

Any ideas? :(

---

### Post by ArtF10 on 2007-08-29
Hey Nick, thanks for the XUbuntu/KUbuntu blogs entries.  I have a quick question about the installation process only:

If I;m an XUbuntu user, after I update by
```
 sudo apt-get update
```
I just want to confirm that it is recommended that my next command is
```
sudo apt-get install compiz-plugins compiz-fusion-plugins-main compiz-fusion-plugins-extra compizconfig-settings-manager sexy-python emerald emerald-themes
```

Then, I will remove the repository through:
```
 sudo nano /etc/apt/sources.list
```

I am new to Linux which is why I just want to confirm that these are the 3 steps that I will follow.  Please let me know if this is correct.

---

### Post by ozzyprv on 2007-08-30
> **stillious said:**
> Hi,
... I Have the problem of missing title bar & menu bar.
...
n.b I use an Nvidia graphics card with the latest drivers installed.
Any ideas? :(
and
> **quattroman said:**
> I got some trouble with compiz + firefox. I get a white borther around it covering the title bar and the close, max, min buttons.
please look at the pic for more reference.
Thanks

It seems like guys lost your borders too. Try the solution from post #42 and solution from bottom of post #54.

---

### Post by ubrox on 2007-08-30
awesome guide. way to go!

---

### Post by Forlong on 2007-08-30
> **Goodson1974 said:**
> This is what I get when I enter ls ~/.config/autostart in the terminal

mat@mat-desktop:~$ ls ~/.config/autostart
beagled.desktop
Alright, then let's do this the hard way. Type this in the terminal:
```
gedit ~/.config/autostart/compiz.desktop
```
There you paste:
```
[Desktop Entry]
Name=Compiz
Encoding=UTF-8
Version=1.0
Exec=compiz --replace
X-GNOME-Autostart-enabled=true
```
and click Save.
Then you restart your XServer via [Ctrl]+[Alt]+[Backspace] and see if it works.
> **quattroman said:**
> I got some trouble with compiz + firefox. I get a white borther around it covering the title bar and the close, max, min buttons.
Just when you thought you've seen everything... ;)
Is that only happening to Firefox? What kind of graphics card are you using?
> **stillious said:**
> I Have the problem of missing title bar & menu bar.
What's the output, when you start ```
gtk-window-decorator
```
separately in a terminal? Your xorg.conf looks OK to me (maybe remove the triplebuffer thing again). But as I said, I'm not a Nvidia user, so I might miss something.
> **ArtF10 said:**
> I am new to Linux which is why I just want to confirm that these are the 3 steps that I will follow.  Please let me know if this is correct.
Yes, that's correct. I recommend using mousepad instead of nano for you, though.
(nano is horrible for beginners but I had to use a text editor that's intalled on every version of Ubuntu by default)
> **ozzyprv said:**
> It seems like guys lost your borders too. Try the solution from post #42 and solution from bottom of post #54.
Thanks for helping.
As far as I know [this solution](http://ubuntuforums.org/showpost.php?p=3267167&postcount=20) (please use this instead of the one in post #42, as I've read that the triplebuffer thing is not recommended for everyone, so I edited it) and the part at the end of [that posting](http://ubuntuforums.org/showpost.php?p=3272679&postcount=54) will do the same thing. The last one is certainly easier, though.

---

### Post by ArtF10 on 2007-08-30
> **Forlong said:**
> ...I recommend using mousepad instead of nano for you, though.
(nano is horrible for beginners but I had to use a text editor that's intalled on every version of Ubuntu by default)...

mousepad?  IS mouspead lighter than gedit?

---

### Post by Forlong on 2007-08-30
> **ArtF10 said:**
> mousepad?  IS mouspead lighter than gedit?
Yes (because it omits many features - but to change some config files it's more than enough) but the reason I recommended it, is because mousepad is installed by default in Xubuntu, while gedit is not.

---

### Post by ArtF10 on 2007-08-30
> **Forlong said:**
> Yes ... because mousepad is installed by default in Xubuntu, while gedit is not.

So by that you mean ```
sudo mousepad
```?

One more question:

How would you recommend going about installing a dock...say AWM (which is supposed to be the best)....AFTER we have installed Compiz Fusion using your method?  

Do you have any step by step instructions?

---

### Post by Forlong on 2007-08-30
> **ArtF10 said:**
> So by that you mean ```
sudo mousepad
```
That's right :)
> **ArtF10 said:**
> 
One more question:

How would you recommend going about installing a dock...say AWM (which is supposed to be the best)....AFTER we have installed Compiz Fusion using your method?  

Do you have any step by step instructions?
I'm not using AWN. I use (a very early version of) Kiba Dock and the WindowList from Screenlets, so I can't recommend anything there.
I'm not a fan of Docks that try to replace my panels but I might check out AWN again, as it has enormously evolved since the last time I tried it - and if I like it, I might provide a How-To for it. But don't hold your breath. ;)

I plan on doing one for Screenlets next, though (in fact I already did... but it's in german).

---

### Post by ArtF10 on 2007-08-30
Hey, I wouldn't mind a screenlets How-to.  Infact I'd prefer it to a dock.

PS:  Are screenlets better than gdesklets?....which uses up less CPU/memory?

---

### Post by Forlong on 2007-08-30
> **ArtF10 said:**
> Are screenlets better than gdesklets?....which uses up less CPU/memory?
Screenlets are much better than gDesklets and I can't think of an application that uses more CPU/memory than gDesklets (OK, the last part was an exaggeration ;)).
Honestly, the only downside to Screenlets is that it requires a composite manager running (like Compiz).

---

### Post by ArtF10 on 2007-08-30
Ok, Forlong, I installed CF on Xubuntu, however, when I run it using Alt+F2 > compiz --replace, nothing happens.  I logged out and restarteX through Atrl+Alt+Bkspace and changed to an XFCE session as I don't know what it was before....no message came up saying change session, should it be default so I that means it was XFCE before as well.

Then Alt+F2 and nothing happens...no cube, nothing.

In Window decoration I had entered emerald so I tried emerald --replace but still nothing.

Any ideas?

---

### Post by Forlong on 2007-08-30
What graphics card do you use and which driver?

---

### Post by ArtF10 on 2007-08-30
ok I got it....I had to restart after enabling Composite in xorg.conf.  I;'ve got Window borders after making the adjustment you recommended in post #42.

HOWEVER, the cube does not show up....infact there is only ONE workspace.  So I cannot rotate or anything.  Any suggestions?  I've gone to ccsm and changed 2 to 4 for Horizontal Size.

---

### Post by ozzyprv on 2007-08-30
> **Forlong said:**
> That's right :)
...
I plan on doing one for Screenlets next, though (in fact I already did... but it's in german).

I am so looking forward to using that HOW-TO. hmmm, German,....where is it? I could try the google translator!.

---

### Post by Forlong on 2007-08-30
> **ArtF10 said:**
> HOWEVER, the cube does not show up....infact there is only ONE workspace.  So I cannot rotate or anything.  Any suggestions?  I've gone to ccsm and changed 2 to 4 for Horizontal Size.
And the other two are set to **1**?
Did you check if the Backend is set to Flat-file?
What about other settings you change in CCSM?

btw: don't worry about what the workspace switcher shows you, I remember having problems with that one on Xfce, too.
But the cube should be working nonetheless (when you enabled all the necessary plugins regarding the cube).
Always try [Ctrl]+[Alt]+[Left Mouseclick]
> **ozzyprv said:**
> I am so looking forward to using that HOW-TO. hmmm, German,....where is it? I could try the google translator!.
It's located here: [http://wiki.ubuntuusers.de/Desklets#Screenlets](http://wiki.ubuntuusers.de/Desklets#Screenlets)
**But I really wouldn't recommend using a translated how-to to install something.**

---

### Post by ArtF10 on 2007-08-30
> **Forlong said:**
> And the other two are set to **1**?
Did you check if the Backend is set to Flat-file?

Yes, the other two are set to 1.  And I made sure that Backend was set to Flat-File.  One thing I remembered, too late ofcourse, was that when I followed your Ubuntu blog version, I manually changed the # of workspaces on the desktop to 4...it was 2 originally.  After changing it to 4 I went ahead with the Compiz Fusion installation.  HOWEVER, with this XUbuntu version, I could not set the workspaces to 4 because there were already 4 squares showing up in the bottom panel after installing.  AFTER installing it on XUbuntu, I went to System(or Settings)> Workspace Settings and changed it from 1 to 4.  I then tried the cube and nothing happened.  Perhaps I should have done this(System>Workpace Settings) before installing CF?

I even tried Ctrl+Alt+Down Arrow and I got the lineup of workspaces showing up like they should, HOWEVER, I could not get them to scroll from left to right or right to left using the arrow keys with Ctrl+Alt still pressed.

> 
What about other settings you change in CCSM?

I just used the ones you listed in the blog....they worked fine for me in Ubuntu, so I wanted to use the same ones here in Xubuntu.  They show up fine...everything is as it should be in terms of other effects.

> btw: don't worry about what the workspace switcher shows you, I remember having problems with that one on Xfce, too.
But the cube should be working nonetheless (when you enabled all the necessary plugins regarding the cube).
Always try [Ctrl]+[Alt]+[Left Mouseclick]

One more question....in Window Decoration should I have entered gtk-window-manager or emerald?  I entered emerald and it didn;t work but when I switched to gtk, it worked.  Also, I tried to run emerald --replace and again, nothing happened but compiz --replace it worked.  Maybe going back and forth between these could have messed up the cube settings?

---

### Post by Goodson1974 on 2007-08-30
Hi Forlong

It worked a treat!

Many thanks for your help, you are a star!!

---

### Post by Forlong on 2007-08-30
> **ArtF10 said:**
> I even tried Ctrl+Alt+Down Arrow and I got the lineup of workspaces showing up like they should, HOWEVER, I could not get them to scroll from left to right or right to left using the arrow keys with Ctrl+Alt still pressed.
Sounds like you didn't enable the **Rotate Cube** plugin.
> **ArtF10 said:**
> One more question....in Window Decoration should I have entered gtk-window-manager or emerald?  I entered emerald and it didn;t work but when I switched to gtk, it worked.  Also, I tried to run emerald --replace and again, nothing happened but compiz --replace it worked.
What output do you get, when running
```
emerald --replace
```
in the terminal?

---

### Post by ArtF10 on 2007-08-30
ok got the cube.  I reformatted and reinstalled Xubuntu...yeah I know, that is pretty extreme but I wanted to be sure.  I then made my selections from ccsm and changed the Settings>Workspaces option to 4.  I then restarted and Alt+F2 gave me the effects...which included the cube.

One last question, how do I add "compiz --replace" to startup programs becasue there is no option to do this like with Ubuntu?

---

### Post by Bart_D on 2007-08-30
Forlong, great tutorial.  I've tried the Xubuntu and ubuntu versions and they worked ok with one exception:

my terminal has become useless. it is now a white screen without a prompt so I cannot enter commands.  I am using Ubuntu Fiesty.  Do you have any suggestions?  I have the latest NVIDIA drivers (GeForce FX 5200) installed and they are working fine.  I need the terminal to get back my window borders and cannot enter anything without a properly working terminal.

---

### Post by Forlong on 2007-08-30
> **ArtF10 said:**
> One last question, how do I add "compiz --replace" to startup programs becasue there is no option to do this like with Ubuntu?
Sorry, I haven't used Xfce since Edgy, so I can't help you there. But I guess any Xubuntu user on the forum might help you out.
> **Bart_D said:**
> my terminal has become useless. it is now a white screen without a prompt so I cannot enter commands.  I am using Ubuntu Fiesty.  Do you have any suggestions?
Did you do, what I wrote in the troubleshooting section [here](http://forlong.blogage.de/article/2007/8/29/How-to-set-up-Compiz-Fusion)?
Make sure you have this line in the **Section "Screen"** of your xorg.conf
```
Option      "AddARGBGLXVisuals"      "True"
```

---

### Post by Bart_D on 2007-08-30
Ok I;'ve got the terminal back, but the window borders are still missing.  I added that line for Nvidia users and that's what brought back the terminal but I still did  not get back the borders.

---

### Post by bigbee79 on 2007-08-30
> **Forlong said:**
> Regarding the window boarder problem with nvidia:

Try adding these options to your xorg.conf.
You need to be root to modify that file:
```
sudo gedit /etc/X11/xorg.conf
```
Look for the **Section "Device"** and add
```
Option      "AddARGBGLXVisuals" "true"
```
You should also make sure your **DefaultDepth** (in *Section "Screen"*) is set to **24**

I'm not a nvidia user, though... so I can't test whether it should work or not.

I'm using nvidia on a f572us Compaq laptop that I recently bought and this worked for me!  Thank you so much.  Not to sound dumb, but being a recent Vista user I really missed having a pretty desktop.  Having compiz working has totally made a Ubuntu user of me.  

Thank you so much!  I love Ubuntu, and I love these forums!!!!

*My only wish is that there was a way for Emerald to start up by default without the window borders going away.  But typing in "emerald --replace" after I start up really isn't too much of a hassle

---

### Post by MrManican on 2007-08-30
a little confused here but in your instructions you say, 

[I]"Adding the Repository

Click on Settings and choose Repositories - that will start the "Software Sources" application where you click on the Third Party Software tab and choose Add... "[/I]

This is where I am confused as I can't seem to find any "Settings" to click on. I don't see it under System/Places/or Applications anywhere. Am I missing this somewhere?

Thanks in advance for any help.

-----------------------

alright, I guess I just need to be more thorough in my reading as I just reread the instructions and I figured it out! Thanks though!

---

### Post by BottomsUp on 2007-08-30
To the OP. Thanks so much for this guide. I had posted earlier in the thread that I was having problems, but after a fresh install, installing XGL per the official ubuntu guides, and following your guide I now have 3D accel with my ATI X1900 plus Compiz Fusion.   Rock on....  Thanks!

---

### Post by MrManican on 2007-08-30
When I press alt+f2 I get nothing. So I tried it through the terminal and I got this message:

"Checking for Xgl: not present. 
Checking for texture_from_pixmap: not present. 
Trying again with indirect rendering:
Checking for texture_from_pixmap: not present. 
aborting and using fallback: /usr/bin/metacity 
Window manager warning: "" found in configuration database is not a valid value for keybinding "toggle_shaded"
" 

Any ideas?


got this too, just needed to update my ATI information... which you also cover! Thanks for everything... I definitely don't feel so Blah anymore!

---

### Post by BottomsUp on 2007-08-31
> **MrManican said:**
> When I press alt+f2 I get nothing. So I tried it through the terminal and I got this message:

"Checking for Xgl: not present. 
Checking for texture_from_pixmap: not present. 
Trying again with indirect rendering:
Checking for texture_from_pixmap: not present. 
aborting and using fallback: /usr/bin/metacity 
Window manager warning: "" found in configuration database is not a valid value for keybinding "toggle_shaded"
" 

Any ideas?


got this too, just needed to update my ATI information... which you also cover! Thanks for everything... I definitely don't feel so Blah anymore!

Do you have XGL and fgrlx installed?

---

### Post by GSF1200S on 2007-08-31
This is making me angry. So, I installed all the required things, and my borders dissapeared. I added the options to xorg.conf, as I always had to do with Beryl, and still no joy. I then added Kde window manager to the command section of window decoration from ccsm. Now, no matter what I do, compiz --replace doesnt work. It WORKED before, it just made my window decorations dissapear. Now, it doesnt work at all, even If i leave command blank.

It gives me the following error in the terminal:
Checking for Xgl: not present.
Checking for texture_from_pixmap: present.
Checking for non power of two support: present.
Checking for Composite extension: present.
Checking for nVidia: present.
Checking for Xgl: not present.

So of course, I installed xserver-xgl, and it still gives me the same error.

I dont know why I would need xgl... I have an Nvidia card and my video drivers work just fine. Ive never used xgl for anything... I always used nvidia or aiglx on beryl. I havent installed any beryl/compiz on this install. Im running KDE... what the hell?:mad:

---

### Post by Forlong on 2007-08-31
> **Bart_D said:**
> Ok I;'ve got the terminal back, but the window borders are still missing.  I added that line for Nvidia users and that's what brought back the terminal but I still did  not get back the borders.
Sorry, I can't tell you more, than what I already said in this thread (and on the blog).
Just make sure your default depth is set to 24 and follow the "first steps".

I hope this will help you out.
> **bigbee79 said:**
> *My only wish is that there was a way for Emerald to start up by default without the window borders going away.  But typing in "emerald --replace" after I start up really isn't too much of a hassle
Did you notice the part about running Compiz with Emerald by default?


@GSF1200S: you certainly do not need Xgl.
Please make sure your xorg.conf is configured properly.
The driver should be "nvidia" and try specifically enabling composite with
```
Option    "Composite"      "Enable"
```
in the **Section "Extensions"**

You can post your xorg.conf if you like and we'll see, if we can help you out.

---

### Post by patambrosio on 2007-08-31
another good way of installing compizFusion on your machine is using the guide that came from the compiz website.
[Compiz.org :: Compiz and Compiz Fusion GIT Ubuntu Repository - Compiz]("http://www.compiz.org/Compiz_and_Copmiz_Fusion_GIT_Ubuntu_Repository")

i also made a much detailed howto, based on the howto i linked above.
[ubuntu chocolate : HOWTO install compiz fusion on ubuntu feisty fawn]("http://ubuntuchocolate.wordpress.com/2007/08/30/howto-install-compiz-fusion-on-ubuntu-feisty-fawn/")

---

### Post by XTREEM|RAGE on 2007-08-31
does the xgl eat a lot of resources, with this guide? Because i have followed another guide and it worked, but it eat like 45% of mine processor :x, when the effects are happening.

rig:
AMD athlon 2800+
ATi X1950
2 gig ram
Asrock K7s8x

It should not eat a lot of resources, not?

english > me >_<

---

### Post by Forlong on 2007-08-31
> **XTREEM|RAGE said:**
> does the xgl eat a lot of resources, with this guide? Because i have followed another guide and it worked, but it eat like 45% of mine processor :x, when the effects are happening.
Hm... the amount of resources used should not depend on the way you installed Compiz. But it's worth a try.
I know Xgl can be a pain in the *** but 45% is certainly a lot :shock:


@patambrosio: please do not promote the git repository here!
One of the main reasons why I wrote this How-To was to prevent users from installing such unstable packages.

---

### Post by ArtF10 on 2007-08-31
> **patambrosio said:**
> another good way of installing compizFusion on your machine is using the guide that came from the compiz website.
[Compiz.org :: Compiz and Compiz Fusion GIT Ubuntu Repository - Compiz]("http://www.compiz.org/Compiz_and_Copmiz_Fusion_GIT_Ubuntu_Repository")

That's trevino's repository.  I simply didn't like it.  IT wasn't stable for me.

---

### Post by Forlong on 2007-08-31
I updated the guides a little bit.
Added some icons and screenshots of the ring/shift switchers.
There's also a new transparency section in the [set-up entry](http://forlong.blogage.de/article/2007/8/29/How-to-set-up-Compiz-Fusion).

I hope you like it.


P.S.: as I noticed in my referral log, that my How-to got posted on [StumbleUpon](http://www.stumbleupon.com/url/forlong.blogage.de/article/2007/8/26/The-best-way-to-install-Compiz-Fusion-on-Ubuntu-Feisty) and [digg](http://digg.com/linux_unix/Install_stable_packages_for_Compiz_Fusion_on_Ubuntu_Feisty_for_beginners).
I'm really greatful for that, but please don't refer to the packages as stable. Although I said in the introduction, that these are the *most stable* ones you can get, you should keep in mind, there's not an official stable release yet.

---

### Post by ArtF10 on 2007-08-31
Forlong, how do I install a custom theme on Xubuntu?  I am using gtk-window-manager, NOT emerald.  I'm running compiz --replace  aned when I select a theme from Emerald manager, nothing happens.

If Emerald manager cannot be used this way, how would I remove it?

---

### Post by GSF1200S on 2007-08-31
> **Forlong said:**
> Sorry, I can't tell you more, than what I already said in this thread (and on the blog).
Just make sure your default depth is set to 24 and follow the "first steps".

I hope this will help you out.

Did you notice the part about running Compiz with Emerald by default?


@GSF1200S: you certainly do not need Xgl.
Please make sure your xorg.conf is configured properly.
The driver should be "nvidia" and try specifically enabling composite with
```
Option    "Composite"      "Enable"
```
in the **Section "Extensions"**

You can post your xorg.conf if you like and we'll see, if we can help you out.

haha.. thanks for the help. I had already added that, and it didnt work. Instead, I went into adept and selected every package for a reinstall, and upgraded all that needed to be upgraded. Then, compiz fusion worked and my borders were present. Kwin +compiz makes for a very nice combo.

I then had a problem with the settings manager. For some really stupid reason I was using sudo instead of Alt F2 or kdesu, so the settings manager didnt have the authority to change my options. Once using kdesu, it worked without a hitch. 

No the only problems I have with compiz is that Firefox wont open a link from kontact... it acts like its trying, but it fails. It also wont let alltray work (which im aware never works with a compositing manager), and frostwire is all white, which im aware is a conflict with Java. Compiz fusion really looks nice though- the window/tab grouping in my mind is a revolution in the way computing is done.

I also have to get the compiz workspace switcher,,, having 16 buttons on the bottom is annoying...

---

### Post by BottomsUp on 2007-08-31
Hi,

I have to type ***emerald --replace*** after each time I change a theme for it to take effect. is this normal or should it change as soon as I click on it?

Thanks

---

### Post by GSF1200S on 2007-08-31
> **BottomsUp said:**
> Hi,

I have to type ***emerald --replace*** after each time I change a theme for it to take effect. is this normal or should it change as soon as I click on it?

Thanks

Sounds normal to me.. The theme stays for good after that right? I would think that emerald would need to be replaced for the changes to take effect. Dont take my word for it though.. I use kwin with Compiz.

---

### Post by ArtF10 on 2007-08-31
Forlong, I've attached a file (Ubuntu Fiesty screenshot).

I tried adjusting transparency as you say and got the dropdown menus to match the panels fine.  But is there a way for the **start** menu to **ALSO** be transparent(say 85% like you say) because it looks a bit funny to have transparent panels with opaque **Start menu items**, like in the picture attached.

---

### Post by anandanbu on 2007-08-31
Wonderful guide for the installation of Compiz Fusion.
Thanks Forlong :)

---

### Post by bmannering on 2007-08-31
This guide is great my only problem is that i cannot get the cube to be a cube, it just has two surfaces... Any help on trying to fix this problem would be great i couldnt find anything about that worked...

---

### Post by beyboo on 2007-08-31
> **bmannering said:**
> This guide is great my only problem is that i cannot get the cube to be a cube, it just has two surfaces... Any help on trying to fix this problem would be great i couldnt find anything about that worked...

Try this - 

CompizConfig Settings manager > General Options > Desktop Size

Horizontal Virtual Size = 4
Vertical Virtual Size = 1 
Number of Desktops = 1

---

### Post by ArtF10 on 2007-08-31
Before doing that, check that you have 4 workspaces in the bottom/top panel...most likely bottom.

---

### Post by n3tfury on 2007-09-01
> **ArtF10 said:**
> Before doing that, check that you have 4 workspaces in the bottom/top panel...most likely bottom.

i just had the same question as bmannering, thanks for the tip which worked - and thanks a ton to forlong for such a painless guide.

---

### Post by Club17 on 2007-09-01
Thank you. I will try this. Have the same problem with my nv 6200.

---

### Post by Forlong on 2007-09-01
Hi,

first of all: I updated the [set-up guide]("http://forlong.blogage.de/article/2007/8/29/How-to-set-up-Compiz-Fusion").
If you have troubles with Xgl eating too much resources, check the troubleshooting section.
And if you want your Main Menu to be transparent, see the new comment in the Transparency guide.


> **ArtF10 said:**
> Forlong, how do I install a custom theme on Xubuntu?  I am using gtk-window-manager, NOT emerald.
Then you have to run
```
gnome-theme-manager
```
(via [Alt]+[F2]) and change it there.
> **ArtF10 said:**
> I'm running compiz --replace  aned when I select a theme from Emerald manager, nothing happens.
Yeah, Emerald Theme Manager can be pretty buggy. Try restarting Emerald and/or Compiz after you have selected a theme.
> **ArtF10 said:**
> If Emerald manager cannot be used this way, how would I remove it?
If you want to remove Emerald Theme Manager, you'll have to remove Emerald. The theme manager is part of the package.
> **GSF1200S said:**
> I then had a problem with the settings manager. For some really stupid reason I was using sudo instead of Alt F2 or kdesu, so the settings manager didnt have the authority to change my options. Once using kdesu, it worked without a hitch.
Do not, never, ever, use CCSM with sudo/kdesu/gksu!
Delete the config folder:
```
sudo rm -r ~/.config/compiz/compizconfig
```
And try running ccsm without being root this time.
> **GSF1200S said:**
> having 16 buttons on the bottom is annoying...
Did you try to change that in ccsm (like said in my set-up guide) and/or in the workspace switcher itself?
If this still doesn't do you any good, try running Compiz via:
```
compiz --replace --ignore-desktop-hints
```
and please let me know if it works for you.
> **bmannering said:**
> my only problem is that i cannot get the cube to be a cube, it just has two surfaces...
Guess what? There's a section in the [set-up guide]("http://forlong.blogage.de/article/2007/8/29/How-to-set-up-Compiz-Fusion") called "Getting the cube". ;)
But thanks, beyboo, for helping out. :)

---

### Post by patambrosio on 2007-09-01
sorry there. i did not mean to.

anyways, i'm trying out your guide and repo. i'll blog and update it if it works for me. thanks!  :)

---

### Post by patambrosio on 2007-09-01
It's working, like magic, i didn't get any errors, or had any problems or things to tweak.
but i've got one problem, **how do i add workspaces?** i only have two. in my previous compiz installation, i had four (makes four faces of the cube). 

thanks to this guide, and thanks in advanced for the help.

---

### Post by Forlong on 2007-09-01
> **patambrosio said:**
> I've got one problem, **how do i add workspaces?** i only have two. in my previous compiz installation, i had four (makes four faces of the cube).
Just check out the following guide to set up Compiz Fusion: [http://forlong.blogage.de/article/2007/8/29/How-to-set-up-Compiz-Fusion](http://forlong.blogage.de/article/2007/8/29/How-to-set-up-Compiz-Fusion) :)

---

### Post by patambrosio on 2007-09-01
it's working perfectly now, and i've got emerald now. i'll be blogging your links. many thanks. :D

---

### Post by n3tfury on 2007-09-01
> **Forlong said:**
> Hi,


Guess what? There's a section in the [set-up guide]("http://forlong.blogage.de/article/2007/8/29/How-to-set-up-Compiz-Fusion") called "Getting the cube". ;)
But thanks, beyboo, for helping out. :)

did you just add that in the past few days because i bookmarked that page and firefox has been up for a couple of days.  i SWEAR that wasn't in there!

---

### Post by ArtF10 on 2007-09-01
Thanks for that transparency tip Forlong.  **[COLOR="Red"][COLOR="Navy"]W H A T  A  G R E A T  T H R E A D.[/COLOR][/COLOR]**

---

### Post by ozzyprv on 2007-09-01
> **ArtF10 said:**
> Thanks for that transparency tip Forlong.  **[COLOR="Red"][COLOR="Navy"]W H A T  A  G R E A T  T H R E A D.[/COLOR][/COLOR]**

Concur.

---

### Post by Forlong on 2007-09-01
> **n3tfury said:**
> did you just add that in the past few days because i bookmarked that page and firefox has been up for a couple of days.  i SWEAR that wasn't in there!
LOL, no it has been there from the beginning but as I pointed out in the How-To, I had to move it (because otherwise I would've had to paste it in the alternative How-To as well).

---

### Post by ozzyprv on 2007-09-01
OFF TOPIC.

Forlong, any suggestion for the Screenlets. I installed it, but there are very few screenlets with version 0.0.10.

---

### Post by Forlong on 2007-09-02
Here is a package with lots of other Screenlets, that you can use with the latest version: [http://forum.compiz-fusion.org/showthread.php?t=3460](http://forum.compiz-fusion.org/showthread.php?t=3460)

If you have troubles installing them, just ask.

---

### Post by GSF1200S on 2007-09-02
> **Forlong said:**
> Hi,

first of all: I updated the [set-up guide]("http://forlong.blogage.de/article/2007/8/29/How-to-set-up-Compiz-Fusion").
If you have troubles with Xgl eating too much resources, check the troubleshooting section.
And if you want your Main Menu to be transparent, see the new comment in the Transparency guide.



Then you have to run
```
gnome-theme-manager
```
(via [Alt]+[F2]) and change it there.

Yeah, Emerald Theme Manager can be pretty buggy. Try restarting Emerald and/or Compiz after you have selected a theme.

If you want to remove Emerald Theme Manager, you'll have to remove Emerald. The theme manager is part of the package.

Do not, never, ever, use CCSM with sudo/kdesu/gksu!
Delete the config folder:
```
sudo rm -r ~/.config/compiz/compizconfig
```
And try running ccsm without being root this time.

Did you try to change that in ccsm (like said in my set-up guide) and/or in the workspace switcher itself?
If this still doesn't do you any good, try running Compiz via:
```
compiz --replace --ignore-desktop-hints
```
and please let me know if it works for you.

Guess what? There's a section in the [set-up guide]("http://forlong.blogage.de/article/2007/8/29/How-to-set-up-Compiz-Fusion") called "Getting the cube". ;)
But thanks, beyboo, for helping out. :)

That doesnt work by itself, but neither does the compiz workspace pager. For me, though, using both the:
compiz --replace --ignore-desktop-hints
seems to do the trick. I deleted that directory, but I might as well ask why its so bad to go root on something like that? Bad habit to do all the time, but im the one making the mods... maybe im missing something.. let me know.
Thanks for that command :)

---

### Post by Forlong on 2007-09-02
> **GSF1200S said:**
> I deleted that directory, but I might as well ask why its so bad to go root on something like that? Bad habit to do all the time, but im the one making the mods... maybe im missing something.. let me know.
Well the most obvious reason not to use such applications with root, is that you exclude yourself from (specific parts of) your home folder.
But it has some safety-related issues as well, see: [https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)
Keep in mind why there is such a thing as sudo anyway. We don't want ourselves to open the floodgates for backdoor programs and the like.
You can be sure, you (or anybody else) can't do any harm to your system, while not being root, because you have (and therefore anyone, that *might* have hacked you, has) only access to your home folder.

---

### Post by pingwayz on 2007-09-03
i have encountered the same error. i received this message from terminal after attempting to run compiz --replace 

Checking for Xgl: not present. 
Checking for texture_from_pixmap: not present. 
Trying again with indirect rendering:
Checking for texture_from_pixmap: not present. 
aborting and using fallback: /usr/bin/metacity 
Window manager warning: "" found in configuration database is not a valid value for keybinding "toggle_shaded"

i have an ATI radeon x800 video card and the fglrx driver installed.. this is what my xorg.conf looks like:

Section "Extensions"
Option "Composite" "true"
EndSection

Section "Device"
	Identifier	"ATI Technologies Inc R420 JI [Radeon X800PRO]"
	Driver		"fglrx"
	Busid		"PCI:1:0:0"
EndSection

Section "Monitor"
	Identifier	"Acer AT3201W"
	Option		"DPMS"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"ATI Technologies Inc R420 JI [Radeon X800PRO]"
	Monitor		"Acer AT3201W"
	Defaultdepth	24
	SubSection "Display"
		Depth	1
		Modes		"1360x768"

---

### Post by Forlong on 2007-09-04
> **pingwayz said:**
> Checking for Xgl: not present. 

[..]

i have an ATI radeon x800 video card and the fglrx driver installed.. 
You need to install and set up [Xgl]("https://help.ubuntu.com/community/CompositeManager/Xgl")


As soon as I have some spare time, I'm going to extend the troubleshooting section.

---

### Post by vlitzer on 2007-09-04
Well first of all, very nice thread and very clear guide. 

I followed it (i have my Nvidia drivers installed from previous Beryl install) but i cant get it to work:

```
~$ compiz --replace
Checking for Xgl: not present. 
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
Checking for nVidia: present. 
Checking for Xgl: not present. 

(gtk-window-decorator:7736): Wnck-WARNING **: Unhandled action type (nil)

(gtk-window-decorator:7736): Wnck-WARNING **: Unhandled action type (nil)

(gtk-window-decorator:7736): Wnck-WARNING **: Unhandled action type (nil)

(gtk-window-decorator:7736): Wnck-WARNING **: Unhandled action type (nil)

(gtk-window-decorator:7736): Wnck-WARNING **: Unhandled action type (nil)

(gtk-window-decorator:7736): Wnck-WARNING **: Unhandled action type (nil)

(gtk-window-decorator:7736): Wnck-WARNING **: Unhandled action type (nil)

(gtk-window-decorator:7736): Wnck-WARNING **: Unhandled action type (nil)

(gtk-window-decorator:7736): Wnck-WARNING **: Unhandled action type (nil)

(gtk-window-decorator:7736): Wnck-WARNING **: Unhandled action type (nil)

(gtk-window-decorator:7736): Wnck-WARNING **: Unhandled action type (nil)

(gtk-window-decorator:7736): Wnck-WARNING **: Unhandled action type (nil)

(gtk-window-decorator:7736): Wnck-WARNING **: Unhandled action type (nil)

(gtk-window-decorator:7736): Wnck-WARNING **: Unhandled action type (nil)

(gtk-window-decorator:7736): Wnck-WARNING **: Unhandled action type (nil)

(gtk-window-decorator:7736): Wnck-WARNING **: Unhandled action type (nil)

(gtk-window-decorator:7736): Wnck-WARNING **: Unhandled action type (nil)

(gtk-window-decorator:7736): Wnck-WARNING **: Unhandled action type (nil)

(gtk-window-decorator:7736): Wnck-WARNING **: Unhandled action type (nil)

(gtk-window-decorator:7736): Wnck-WARNING **: Unhandled action type (nil)
/usr/bin/compiz.real (video) - Warn: No 8 bit GLX pixmap format, disabling YV12 image format
Segmentation fault (core dumped)

```

and this is some core fragments of my xorg config file

```
Section "Module"
    Load           "i2c"
    Load           "bitmap"
    Load           "ddc"
    Load           "extmod"
    Load           "freetype"
    Load           "glx"
    Load           "int10"
    Load           "vbe"
EndSection

```

```

Section "Extensions"
    Option         "Composite" "Enable"
EndSection

```

Im running ubuntu feisty btw.
any clue? 
Thanks in advance

---

### Post by Forlong on 2007-09-04
It's weird that it checks for Xgl again, although everything needed is present.

Did you try the command for Nvidia users in the Troubleshooting section of the "Set up..." guide?


edit: wait, Compiz could be running nonetheless, it doesn't look like an error message to me. Try pressing [Alt] and then scroll down with your mousewheel - does the opacity decrease?

---

### Post by vlitzer on 2007-09-04
no, nothing happen with that.
edit: perhaps i have some old config file of compiz or beryl?

---

### Post by Forlong on 2007-09-04
I booted into my Ubuntu Studio install (where I installed and tested the packages) and checked - this output is nothing to worry about. Compiz should be running!
> **vlitzer said:**
> perhaps i have some old config file of compiz or beryl?
Make sure you followed the **First Steps**!

Then press [Alt]+[F2] and type
```
compiz --replace
```
Then go to **System &#8594; Preferences &#8594; CompizConfig Settings Manager** and enable **Wobbly Windows**

Does it take effect?

---

### Post by vlitzer on 2007-09-04
well first of all thanks for the quick reply!

yes i followed the first steps

and i already tried that one.. because when i run compiz --replace from the console to see the errors, the execution of compiz --replace doesnt end its execution, but i dont see any other clue that proves that its running (wobbly windows doesnt take efects, neither the cube or the other effects)

---

### Post by Forlong on 2007-09-04
Could you please run compiz again and look at **System &#8594; Administartation &#8594; System Monitor &#8594; Processes** if **compiz.real** is listed?

Another good way to check is open the terminal, go to **Edit &#8594; Current Profile &#8594; Effects** and select **Transparent background**. If you can see what's going on below the window, Compiz is runnig.

---

### Post by Cocchiararo on 2007-09-04
hi, i changed from beryl to compiz-fusion after reading this guide, and i pretty much love it XD (i cant find an option to set how far the cube should zoom, but its more or less ok with refrections set tho :P)

i have 1 problem tho... only twice in a couple of days, my desktop (or compiz or whatever, i cant be sure, im new to linux :P), seems to have frozen, but my mouse was still working, and sound too, but i couldnt  do anything, not even go to consoles, so i had to do a hard reset :(

it hasnt happened again, but whats even more anoying, is that the SAME thing happens most of the time when i want to logof/restart/turn of my computer.

here is a screen of how it loocks (form a camera).

[[IMG]http://img249.imageshack.us/img249/4484/untitledam9.th.jpg[/IMG]](http://img249.imageshack.us/my.php?image=untitledam9.jpg)

(i like vista wallpaper, i would like to have the animated version like in vista ultimate tho :P)

any idea why is this happening ?

also, i thought that maybe, i could fix this by activating the crash handler plugin, but i have no idea what to type into the textbox :P (i think that beryl had no texbox, and it presented me with options, wich i dont remember :P )

thx in advance, and great guide.

---

### Post by Forlong on 2007-09-04
> **Cocchiararo said:**
> i cant find an option to set how far the cube should zoom
CCSM &#8594; Rotate Cube &#8594; Zoom


As for the freeze issue: I remember reading something about a Nvidia driver having issues with indirect rendering.

Open the startscript for Compiz:
```
sudo gedit /usr/bin/compiz
```
look for the line about "No indirect by default" and change it to
```
INDIRECT=0
```


Please let me know if this works for you.

---

### Post by cursebg on 2007-09-04
> **Forlong said:**
> To everyone having problems with their titlebars on nvidia, try this:
```
sudo nvidia-xconfig --add-argb-glx-visuals -d 24
```
This should add the proper commands automatically to your xorg.conf

Then press [Ctrl]+[Alt]+[Backspace] to restart your XServer.

Please let me know if this works for you.
thanks, that worked for me :)

---

### Post by Cocchiararo on 2007-09-04
> **Forlong said:**
> CCSM &#8594; Rotate Cube &#8594; Zoom


As for the freeze issue: I remember reading something about a Nvidia driver having issues with indirect rendering.

Open the startscript for Compiz:
```
sudo gedit /usr/bin/compiz
```
look for the line about "No indirect by default" and change it to
```
INDIRECT=0
```


Please let me know if this works for you.

i loged in and out like 5 times in a row with no problems whatsoever... ill report back if the problem comes back (it was kind of random before, but when i did some logout/log in attemts, i got the crash on the 3rd one last time).

thx for you help XD

---

### Post by vlitzer on 2007-09-04
> **Forlong said:**
> Could you please run compiz again and look at **System &#8594; Administartation &#8594; System Monitor &#8594; Processes** if **compiz.real** is listed?

Another good way to check is open the terminal, go to **Edit &#8594; Current Profile &#8594; Effects** and select **Transparent background**. If you can see what's going on below the window, Compiz is runnig.

no, compiz.real is not listed. And with the console transparent it only get transparent with my wallpaper, not with the windows below the console :(

---

### Post by Vorian on 2007-09-05
The repository has changed from dog food to

```
deb http://ppa.launchpad.net/amaranth/ubuntu feisty main
deb-src http://ppa.launchpad.net/amaranth/ubuntu feisty main
```

---

### Post by Cocchiararo on 2007-09-05
so, if we want to install compiz again we have to change it, but still, we must remove it after instaling it cause it wants to update forever ?

pd: do i lose performance or features or something by disabling indirect rendering ? it seems to have fixed my previous problem.

---

### Post by Forlong on 2007-09-05
Hi everybody,

I overhauled the How-To (because of the new location of the repository but some other things as well)

I also added a brand new troubleshooting section to all the guides.


Feedback is appreciated.

Regards,
Nick

---

### Post by Tosa on 2007-09-05
Hm, I've got a problem from the very start. i cant install Compiz... I've tried KDE install and this is what I get!?

> Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  compiz-kde: Depends: libcompizconfig-backend-kconfig but it is not installable
E: Broken packages

---

### Post by greenstar on 2007-09-05
Thanks for the excellent Compiz-Fusion guide. I removed Beryl from my box and installed Compiz-Fusion on it & another box as well. Both went smoothly and as per your guide. 

I'd been seeing the buzz on the web recently about Compiz-Fusion and it lives up to the hype.

:guitar:Compiz-Fusion rocks!

Thanks again,
Greenstar

---

### Post by Forlong on 2007-09-05
> **Tosa said:**
> Hm, I've got a problem from the very start. i cant install Compiz... I've tried KDE install and this is what I get!?

Thanks for the feedback.

Yes, the package seems to be missing in the new repository. I'll contact Amaranth about it.

Try the old one instead:
```
deb http://ppa.dogfood.launchpad.net/amaranth/ubuntu feisty main
```
and let me know if it works for you.

---

### Post by Tosa on 2007-09-05
Thanks!

Unfortunately the old repository has some problems too...

> The following packages have unmet dependencies:
  compiz-core: Breaks: libcompizconfig0 (< 0.5.2+git20070829) but 0.5.2-0ubuntu1                  ~ppa2 is to be installed
  compiz-kde: Depends: compiz-core (= 1:0.5.2-0ubuntu3~ppa4) but 1:0.5.2+git2007                  0829-0ubuntu1~ppa2 is to be installed
              Depends: compiz-plugins (= 1:0.5.2-0ubuntu3~ppa4) but 1:0.5.2+git2                  0070829-0ubuntu1~ppa2 is to be installed
E: Broken packages

:(

---

### Post by Forlong on 2007-09-05
Did you remove the packages you already installed as well as the other repository?

---

### Post by Tosa on 2007-09-05
I did remove the other repository, but I thought they both had the same packages... I'll reinstall everything.

:oops:

---

### Post by Tosa on 2007-09-05
OK,

I've reinstalled it from the old repository and no error messages this time!

Thanks for help.

I've installed xgl, so I guess should take a deep breath and try it...

---

### Post by Morientes on 2007-09-05
When will the new repositories be working - and what is the difference between them and the old repos?

Also, after installing from the old repos, I keep getting an update notice that says compiz-core is a new version. But even though I install it, it keeps saying that the update is there. Any one know what's wrong?

---

### Post by Forlong on 2007-09-05
> **Morientes said:**
> When will the new repositories be working
The new one is working *right now*. If you follow the "original" guide for GNOME users, you shouldn't face a problem.

It's just this one package for KDE users, that's missing in the new repository. I updated ("downdated") the KDE/Xfce guide because of that.

Just follow the guides. They are perfectly safe to use the way they are.
> **Morientes said:**
> and what is the difference between them and the old repos?
I didn't notice anything. The packages from the new guide have later versions but that doesn't mean much. I didn't have the time to do a broad check, though. Maybe tomorrow.
> **Morientes said:**
> Also, after installing from the old repos, I keep getting an update notice that says compiz-core is a new version. But even though I install it, it keeps saying that the update is there. Any one know what's wrong?
It's all in the guide. Please just follow it entirely!


P.S. the update issue hasn't been fixed in the new repo.

---

### Post by Forlong on 2007-09-05
Sorry Cocchiararo, I haven't noticed your posting before.
> **Cocchiararo said:**
> so, if we want to install compiz again we have to change it, but still, we must remove it after instaling it cause it wants to update forever ?
Yes, I'm afraid that's still the case.
> **Cocchiararo said:**
> do i lose performance or features or something by disabling indirect rendering ? it seems to have fixed my previous problem.
You'll definitely won't miss any plugins. And you tell me, if you have any performance issues. :)

---

### Post by vbmds on 2007-09-06
Thanks for putting up this guide Forlong. I've just gone through it and its worked almost flawlessly...except for the Window Title bar and Borders missing issue. I've now got that issue sorted as well and it came down to entering the correct 'command' which every HowTo and Tutorial seems to have different.

So, this was what got my Title bar and borders back: In the CompizConfig Settings Manger, within the Window Decoration module, I entered ***gtk-window-decorator***  into the command field.

---

### Post by Forlong on 2007-09-06
Thanks for the feedback.

Seems like you haven't followed the *first steps*, though. ;)

---

### Post by vlitzer on 2007-09-06
Well i decided to reinstall and follow the guide again; I removed all the packages related with compiz-fusion, tried the new rep dir and reinstalled using your guide without the extras, and it worked! Very nice guide, thanks for your support Forlong :)

---

### Post by vlitzer on 2007-09-06
btw i notice that with compiz-fusion as with beryl, the option for moving the windows to other desktops doesnt exists. Im refering the option in the right button menu on the aplication window "Send to workspace right", or "send to workspace... 1234".. is there a way to activate this functionality?

---

### Post by cmon on 2007-09-06
Hi.
I just followed all the steps in your guide. Everything installed smooth without any errors. But when I hit alt + F2 and type compiz --replace, nothing happens, no cube and no fancy effects :(. 
 Except that my window borders disappear. I have the latest nvidia drivers installed and I've made the suggested changes to my xorg.conf-file. So what can be wrong?

Please help me out...  And thanks for a great and userfriendly guide :)

---

### Post by Forlong on 2007-09-06
> **vlitzer said:**
> i notice that with compiz-fusion as with beryl, the option for moving the windows to other desktops doesnt exists. Im refering the option in the right button menu on the aplication window "Send to workspace right", or "send to workspace... 1234"..
I can confirm this is missing on Compiz. I started a thread on the cf.o forums about it. Maybe somebody knows something about it (if so, I'll report back).

btw: glad to here it finally works for you. :)
> **cmon said:**
> when I hit alt + F2 and type compiz --replace, nothing happens, no cube and no fancy effects :(. 
 Except that my window borders disappear. I have the latest nvidia drivers installed and I've made the suggested changes to my xorg.conf-file. So what can be wrong?
Could you please post the output of
```
compiz --replace
```
in the terminal?

You might want to post your xorg.conf as well.

---

### Post by vlitzer on 2007-09-06
also i found several bugs and some missed functionality compared with gnome. Some drag and drop actions over the desktop switcher for instance, and double clicking on the "Expo plugin" when selecting a desktop causes the compiz to crash (but returns to normal gnome); i should probably report those bugs, where do you recomend me to do so?

---

### Post by Forlong on 2007-09-06
According to a developer, the "move to workspace" feature will probably be included in Gutsy, because it has a newer version of libwnck (which provides it).
Beryl had it, because there was a patched version in it's repository.
> **vlitzer said:**
> also i found several bugs and some missed functionality compared with gnome. Some drag and drop actions over the desktop switcher for instance
Well... Compiz just doesn't have such a feature (and I'm not quite sure if it would be technically possible). You have to keep in mind Compiz is only a window manager (like Metacity, which you probably haven't even heard about).
> **vlitzer said:**
> double clicking on the "Expo plugin" when selecting a desktop causes the compiz to crash (but returns to normal gnome)
I can confirm this but I wonder why you would do this anyway, lol
> **vlitzer said:**
> i should probably report those bugs, where do you recomend me to do so?
That's a tough question. Regarding the Expo-bug, I'm going to test this on my regular install and if it has this bug as well, I'm going to post it to [CFs bugzilla](http://bugs.opencompositing.org/).
But since those are technically Ubuntu packages, you can post them on launchpad... it's just that those are backports, so I'm not sure if it's OK. It should be definitely mentioned.

---

### Post by cmon on 2007-09-06
The command ```
compiz --replace
``` gives no output at all in my terminal. The only thing that happen is that my screen blinks once and then my window borders disappear.

Here's my xorg-file:
```
# nvidia-xconfig: X configuration file generated by nvidia-xconfig
# nvidia-xconfig:  version 1.0  (buildmeister@builder3)  Sat May 26 01:04:16 PDT 2007

# /etc/X11/xorg.conf (xorg X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the xorg.conf(5) manual page.
# (Type "man xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "ServerLayout"
    Identifier     "Default Layout"
    Screen         "Default Screen" 0 0
    InputDevice    "Generic Keyboard"
    InputDevice    "Configured Mouse"
    InputDevice    "stylus" "SendCoreEvents"
    InputDevice    "cursor" "SendCoreEvents"
    InputDevice    "eraser" "SendCoreEvents"
EndSection

Section "Files"

	# path to defoma fonts
    FontPath        "/usr/share/fonts/X11/misc"
    FontPath        "/usr/share/fonts/X11/cyrillic"
    FontPath        "/usr/share/fonts/X11/100dpi/:unscaled"
    FontPath        "/usr/share/fonts/X11/75dpi/:unscaled"
    FontPath        "/usr/share/fonts/X11/Type1"
    FontPath        "/usr/share/fonts/X11/100dpi"
    FontPath        "/usr/share/fonts/X11/75dpi"
    FontPath        "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
    Load           "bitmap"
    Load           "ddc"
    Load           "extmod"
    Load           "freetype"
    Load           "glx"
    Load           "int10"
    Load           "vbe"
EndSection

Section "InputDevice"
    Identifier     "Generic Keyboard"
    Driver         "kbd"
    Option         "CoreKeyboard"
    Option         "XkbRules" "xorg"
    Option         "XkbModel" "pc105"
    Option         "XkbLayout" "se"
EndSection

Section "InputDevice"
    Identifier     "Configured Mouse"
    Driver         "mouse"
    Option         "CorePointer"
    Option         "Device" "/dev/input/mice"
    Option         "Protocol" "ExplorerPS/2"
    Option         "ZAxisMapping" "4 5"
    Option         "Buttons" "7"
    Option         "ButtonMapping" "1 2 3 6 7"
    Option         "Resolution" "800"
    Option         "Emulate3Buttons" "false"
EndSection

Section "InputDevice"
    Identifier     "stylus"
    Driver         "wacom"
    Option         "Device" "/dev/input/wacom"
    Option         "Type" "stylus"
    Option         "ForceDevice" "ISDV4"		# Tablet PC ONLY
EndSection

Section "InputDevice"
    Identifier     "eraser"
    Driver         "wacom"
    Option         "Device" "/dev/input/wacom"
    Option         "Type" "eraser"
    Option         "ForceDevice" "ISDV4"		# Tablet PC ONLY
EndSection

Section "InputDevice"
    Identifier     "cursor"
    Driver         "wacom"
    Option         "Device" "/dev/input/wacom"
    Option         "Type" "cursor"
    Option         "ForceDevice" "ISDV4"		# Tablet PC ONLY
EndSection

Section "Monitor"
    Identifier     "Allmän skärm"
    HorizSync       30.0 - 100.0
    VertRefresh     50.0 - 160.0
    Option         "DPMS"
EndSection

Section "Device"
    Identifier     "NVIDIA GeForce 6600"
    Driver         "nvidia"
EndSection

Section "Screen"
    Identifier     "Default Screen"
    Device         "NVIDIA GeForce 6600"
    Monitor        "Allmän skärm"
    DefaultDepth    24
    Option         "AddARGBGLXVisuals" "True"
    SubSection     "Display"
        Depth       1
        Modes      "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       4
        Modes      "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       8
        Modes      "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       15
        Modes      "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       16
        Modes      "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       24
        Modes      "1280x1024" "1024x768" "800x600" "640x480"
    EndSubSection
EndSection

Section "Extensions"
    Option         "Composite" "Enable"
EndSection

```

---

### Post by MrWookie on 2007-09-06
I'm having a problem following your directions to use the gtk window decorator.  If I try to install the compiz-gtk package that contains the gtk window decorator, it says "Depends: compiz-core (=1:0.3.6-1ubuntu13) but 1:0.5.2+git20070829-0ubuntu1amaranth1 is to be installed"

I don't seem to have the option to install version 1:0.3.6-1ubuntu13 of the compiz-core, so if I try to follow your guide, I end up with the borderless windows.  Any ideas?

---

### Post by Forlong on 2007-09-06
> **cmon said:**
> The command ```
compiz --replace
``` gives no output at all in my terminal.
That is very weird. Did you really remove all previous Compiz packages and third-party repositories?
> **MrWookie said:**
> I'm having a problem following your directions to use the gtk window decorator.  If I try to install the compiz-gtk package that contains the gtk window decorator, it says "Depends: compiz-core (=1:0.3.6-1ubuntu13) but 1:0.5.2+git20070829-0ubuntu1amaranth1 is to be installed"
Please do not install any packages not mentioned in the guide.
The gtk-window-decorator is included in the **compiz** (meta-)package.
> **MrWookie said:**
> if I try to follow your guide, I end up with the borderless windows.
Did you follow the *first steps*?
If you have a Nvidia card, check out the troubleshooting section - there's a set up command that might help.

---

### Post by vlitzer on 2007-09-06
> **Forlong said:**
> I can confirm this but I wonder why you would do this anyway, lol.

hehe well i double clicked on a desktop because i wanted to "select" and close the expo view so i can jump between more easily instead of deactivating the explo plugin :P

---

### Post by vbmds on 2007-09-06
Thanks for the response Forlong. As a fairly new user I assume that I need to follow guides word for word so I _did_ indeed complete the first steps of your guide. 

I will say however that I'm running a fairly clean install of ubuntu 7.04 and have not before now installed any other Desktop enhancement packages like compiz/beryl/emerald etc. so the removal steps did not actually do anything according to the Console summary for the commands.

The only thing I can identify that I have different is my graphics driver is nvidia-glx-new (1.0-9755) not nvidia-glx.

Anyways, keep up the good work.

---

### Post by Aundy on 2007-09-06
I am having the exact same problem that Vlitzer had: I can change the settings in CompizConfig and CompizConfig remembers my settings but when I run compiz the settings do not take effect.  It is almost as if compiz is not running at all.  Unfortunately the fix that worked for Vlitzer (reinstalling everything) did not work for me.  Any help/ideas would be greatly appreciated.

---

### Post by Forlong on 2007-09-07
> **vlitzer said:**
> hehe well i double clicked on a desktop because i wanted to "select" and close the expo view so i can jump between more easily instead of deactivating the explo plugin :P
Like I said in the set up guide, you can do that by using the right mousebutton instead of a middle-click.
> **vbmds said:**
> I will say however that I'm running a fairly clean install of ubuntu 7.04 and have not before now installed any other Desktop enhancement packages like compiz/beryl/emerald etc. so the removal steps did not actually do anything according to the Console summary for the commands.
So I assume you used the alternative guide on a KDE or Xfce install?
Anyay, I wasn't talking about the *very first steps* of the guide, but about the **First steps** section. :)
That's where I tell to do the exact same thing you did with the decorator :)
> **Aundy said:**
> I am having the exact same problem that Vlitzer had: I can change the settings in CompizConfig and CompizConfig remembers my settings but when I run compiz the settings do not take effect.  It is almost as if compiz is not running at all.  Unfortunately the fix that worked for Vlitzer (reinstalling everything) did not work for me.  Any help/ideas would be greatly appreciated.
Please post the output of
```
compiz --replace
```
and
```
glxinfo | grep "direct rendering"
```
and
```
grep -v ^# /etc/X11/xorg.conf
```
in the terminal

---

### Post by murak on 2007-09-07
Greate guide! An update made my Compiz Fusion useless and this guide told me how to remove prior Compiz installations + made it simple to get the window borders to "not dissapere". Thank you a lot! I Will recommend this guide to  friends.

---

### Post by Aundy on 2007-09-07
compiz --reaplace gives

Checking for Xgl: not present. 
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
Checking for nVidia: present. 
Checking for Xgl: not present. 

(gtk-window-decorator:14106): Wnck-WARNING **: Unhandled action type (nil)

(gtk-window-decorator:14106): Wnck-WARNING **: Unhandled action type (nil)

(gtk-window-decorator:14106): Wnck-WARNING **: Unhandled action type (nil)

(gtk-window-decorator:14106): Wnck-WARNING **: Unhandled action type (nil)

(gtk-window-decorator:14106): Wnck-WARNING **: Unhandled action type (nil)

(gtk-window-decorator:14106): Wnck-WARNING **: Unhandled action type (nil)

(gtk-window-decorator:14106): Wnck-WARNING **: Unhandled action type (nil)

(gtk-window-decorator:14106): Wnck-WARNING **: Unhandled action type (nil)
/usr/bin/compiz.real: symbol lookup error: /usr/lib/compiz/libdecoration.so: undefined symbol: decor_apply_gravity
Window manager warning: "" found in configuration database is not a valid value for keybinding "toggle_shaded"
-------------------------------------------------------------------------------------------------------------------
glxinfo | grep "direct rendering" gives

direct rendering: Yes

grep -v ^# /etc/X11/xorg.conf gives

Section "Files"
        Fontpath        "/usr/share/fonts/X11/misc"
        Fontpath        "/usr/share/fonts/X11/cyrillic"
        Fontpath        "/usr/share/fonts/X11/100dpi/:unscaled"
        Fontpath        "/usr/share/fonts/X11/75dpi/:unscaled"
        Fontpath        "/usr/share/fonts/X11/Type1"
        Fontpath        "/usr/share/fonts/X11/100dpi"
        Fontpath        "/usr/share/fonts/X11/75dpi"
        # path to defoma fonts
        Fontpath        "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
        Load            "i2c"
        Load            "bitmap"
        Load            "ddc"
        Load            "extmod"
        Load            "freetype"
        Load            "glx"
        Load            "int10"
        Load            "vbe"
EndSection

Section "InputDevice"
        Identifier      "Generic Keyboard"
        Driver          "kbd"
        Option          "CoreKeyboard"
        Option          "XkbRules"      "xorg"
        Option          "XkbModel"      "pc105"
        Option          "XkbLayout"     "us"
EndSection

Section "InputDevice"
        Identifier      "Configured Mouse"
        Driver          "mouse"
        Option          "CorePointer"
        Option          "Device"        "/dev/input/mice"
        Option          "Protocol"      "ImPS/2"
        Option          "ZAxisMapping"  "4 5"
        Option          "Emulate3Buttons"       "true"
EndSection

Section "InputDevice"
        Driver          "wacom"
        Identifier      "stylus"
        Option          "Device"        "/dev/input/wacom"
        Option          "Type"  "stylus"
        Option          "ForceDevice"   "ISDV4"# Tablet PC ONLY
EndSection

Section "InputDevice"
        Driver          "wacom"
        Identifier      "eraser"
        Option          "Device"        "/dev/input/wacom"
        Option          "Type"  "eraser"
        Option          "ForceDevice"   "ISDV4"# Tablet PC ONLY
EndSection

Section "InputDevice"
        Driver          "wacom"
        Identifier      "cursor"
        Option          "Device"        "/dev/input/wacom"
        Option          "Type"  "cursor"
        Option          "ForceDevice"   "ISDV4"# Tablet PC ONLY
EndSection

Section "Device"
        Identifier      "nVidia Corporation NV34 [GeForce FX 5200]"
        Driver          "nvidia"
        Busid           "PCI:1:0:0"
        Option          "AddARGBVisuals"        "True"
        Option          "AddARGBGLXVisuals"     "True"
        Option          "NoLogo"        "True"
EndSection

Section "Monitor"
        Identifier      "Generic Monitor"
        Option          "DPMS"
        Horizsync       28-51
        Vertrefresh     43-60
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Device          "nVidia Corporation NV34 [GeForce FX 5200]"
        Monitor         "Generic Monitor"
        Defaultdepth    24
        Option "AddARGBGLXVisuals" "True"
        SubSection "Display"
                Depth   1
                Modes           "1024x768"      "800x600"       "640x480"
        EndSubSection
        SubSection "Display"
                Depth   4
                Modes           "1024x768"      "800x600"       "640x480"
        EndSubSection
        SubSection "Display"
                Depth   8
                Modes           "1024x768"      "800x600"       "640x480"
        EndSubSection
        SubSection "Display"
                Depth   15
                Modes           "1024x768"      "800x600"       "640x480"
        EndSubSection
        SubSection "Display"
                Depth   16
                Modes           "1024x768"      "800x600"       "640x480"
        EndSubSection
        SubSection "Display"
                Depth   24
                Modes           "1680x1050"     "1024x768"      "800x600"      "640x480"
        EndSubSection
EndSection

Section "ServerLayout"
        Identifier      "Default Layout"
  screen "Default Screen"
        Inputdevice     "Generic Keyboard"
        Inputdevice     "Configured Mouse"
        Inputdevice     "stylus"        "SendCoreEvents"
        Inputdevice     "cursor"        "SendCoreEvents"
        Inputdevice     "eraser"        "SendCoreEvents"
EndSection

Section "DRI"
        Mode    0666
EndSection
---------------------------------------------------------------------------------------------------------------------
Also when I run compiz --replace my gnome panels disappear for a second and the screen flashes.  Absolutely none of the changes I make in CompizConfig take place not even when I change the number of virtual desktops.  The system monitor does list compiz.real under processes.  I amusing ubuntu feisty fawn, and it was fresh off of the installation cd when I tried your guide.

---

### Post by Aundy on 2007-09-07
I just noticed that under the display settings tab in general options in CompizConfig the only listed output is 680x480+0+0, but my screen resolution is set to 1680x1050.

---

### Post by Forlong on 2007-09-07
First of all: thanks for the informations but please use the CODE tag next time. This will limit the space of your posting.
> **Aundy said:**
> /usr/bin/compiz.real: symbol lookup error: /usr/lib/compiz/libdecoration.so: undefined symbol: decor_apply_gravity
Please try to update **libdecoration0** (you'll have to enable the repository again).
In fact, check if there are any other updates available when enabling the repository and update the package informations.

P.S. did you really switch to Flat-file Backend?

P.P.S. don't worry about the resolution, it's set this way on my install as well.

---

### Post by alwiap on 2007-09-07
Hey Forlong,

I used both your FAQ's to set up compiz and I absolutely love it, cheers to you.

I do have one problem.

I followed all your directions to the tee, and I did this as is listed in 'How to set up compiz fusion':
```
Display all virtual desktop when moving the mouse pointer to the top left corner of the screen
Double-click Expo &#8594; Actions &#8594; Bindings &#8594; Expo and choose TopLeft
```

However, every time I move my mouse to the left side of the screen, when I click on any of the 4 workspaces, when I return to which ever one I picked, all the effects of Compiz are turned off and I have to type Ctrl+Alt+BkSpace and then everything is back to normal (compiz works again.)

Anyone else had this problem?  I did mess around with some of the other stuff in ccsm, could that hinder the virtual desktop from working correctly?  Everything else works in compiz just fine.

I hope I'm being clear enough with the description of the problem, please help me out.  I would love to have this feature working all the time :)

---

### Post by Forlong on 2007-09-07
How do you zoom back to the desktop?

The new repository has a bug with the double-click but right-click should work.

---

### Post by alwiap on 2007-09-07
Ok let me explain more clearly :)

I move my cursor all the way to the left of the screen.

I see all four workspaces.

If I move my cursor all the way to the left again, it goes back to my current workspace like it should.

But when I double-click on any other workspace (the 2nd, 3rd, or 4th), it will take me to that workspace, but then none of the compiz stuff works. 

I guess I'm unfortunately triggering the bug when I double-click on a desktop as you said?

So I should just right-click on the desktop I want to go to.

I think I understand now.

---

### Post by Aundy on 2007-09-07
Success!  I uncommented the compiz fusion source in my sources.list, ran sudo apt-get upgrade , libdecoration0 was installed, and now everything works!  Thank you for your help.

---

### Post by MrWookie on 2007-09-07
OK, I see that the metapackage did install the gtk decorator.  I went back and dutifully followed your instructions to the letter, and I'm still getting no window borders.  I tried with both the gtk-window-decorator and with emerald.  I experimented with running your start-compiz script in the console instead of alt-F2, and from the console, it gave me a bunch of error messages that might be useful to someone more familiar with this stuff than I am:

```
Checking for Xgl: not present. \nChecking for texture_from_pixmap: present. \nChecking for non power of two support: present. \nChecking for Composite extension: present. \nChecking for nVidia: present. \nChecking for Xgl: not present. \n/usr/bin/compiz.real (video) - Warn: No 8 bit GLX pixmap format, disabling YV12 image format
/usr/bin/compiz.real (core) - Warn: No GLXFBConfig for depth 32
/usr/bin/compiz.real (resizeinfo) - Warn: Bind Pixmap to Texture failure
/usr/bin/compiz.real (core) - Warn: No GLXFBConfig for depth 32
/usr/bin/compiz.real (resizeinfo) - Warn: Bind Pixmap to Texture failure
/usr/bin/compiz.real (core) - Warn: No GLXFBConfig for depth 32
/usr/bin/compiz.real (core) - Warn: No GLXFBConfig for depth 32
/usr/bin/compiz.real (core) - Warn: No GLXFBConfig for depth 32
/usr/bin/compiz.real (core) - Warn: No GLXFBConfig for depth 32
/usr/bin/compiz.real (core) - Warn: No GLXFBConfig for depth 32
/usr/bin/compiz.real (core) - Warn: No GLXFBConfig for depth 32

(emerald:22677): Wnck-WARNING **: Unhandled action type (nil)

```

The last error message (emerald:22677) is actually repeated 22 times or so, but I trimmed it for brevity.  

I do have an nVidia graphics card, but I ran the script you suggested, and it didn't change the result.  One thing I forgot to mention is that I'm using a dual monitor set up with a desktop that spans the two monitors.  Could that be causing the problem?

---

### Post by Forlong on 2007-09-07
Could you please post the output of
```
grep -v ^# /etc/X11/xorg.conf
```

---

### Post by vbmds on 2007-09-07
Forlong, I think I've found where the No Borders issue may have come from in my case...

In your second Guide named **How to set up Compiz Fusion**, under the trouble shooting section, you have a spelling error with the command that needs to be entered under the Window Decoration module's command field: your guide has ```
gtk-window-decotrator
``` whereas it should be ```
gtk-window-decorator
``` as per the 1st Guide

In the 1st Guide under the First steps, entering the code into the appropriate command line did not work for me. It seems that until I completed the 2nd guide and corrected the spelling error did the command field code work.  

Its really neat being able to take the wind out of the sails of friends who gloat at how great the marvels of Vistas display is, when I show off Compiz Fusion...:lolflag:

---

### Post by Forlong on 2007-09-07
Thanks a lot for pointing out the trypo.
Fixed it immediately.

---

### Post by Cocchiararo on 2007-09-07
> **Forlong said:**
> Sorry Cocchiararo, I haven't noticed your posting before.

Yes, I'm afraid that's still the case.

You'll definitely won't miss any plugins. And you tell me, if you have any performance issues. :)

i see no performance problems :P

but i dont know if its something i configured on a plugin or what, but the alt + mouse wheel for changing transparencies on windows wont work, it works on panels tho. (if i do it on windows, they might turn transparent when they feel like it, but not most of the time :P)

its either the indirect rendering thing, or me messing with something :P

but i really dont care, i dont use that anyway :P

---

### Post by JbsTac on 2007-09-09
Hey Forlong, thanks for the great how to. I followed your instructions and was able to get cf and emerald working for the first time in ages! 

I did run into a little problem though. I'm not sure if it happened when I removed all the compiz/beryl/emerald packages or when I installed cf and emerald. The "restart" and "shutdown" buttons have disappeared from my quit menu. I'm stuck with rebooting and shutting down from the terminal, please help!

---

### Post by Forlong on 2007-09-09
> **JbsTac said:**
> I did run into a little problem though. I'm not sure if it happened when I removed all the compiz/beryl/emerald packages or when I installed cf and emerald. The "restart" and "shutdown" buttons have disappeared from my quit menu. I'm stuck with rebooting and shutting down from the terminal, please help!
That's an Xgl issue - if you haven't installed it just now, you should have noticed that before.
Use this for your startxgl.sh:
```
#!/bin/sh
Xgl :1 -nolisten tcp -fullscreen -ac -br -accel xv:pbuffer -accel glx:pbuffer &
DISPLAY=:1
cookie="$(xauth -i nextract - :0 | cut -d ' ' -f 9)"
xauth -i add :1 . "$cookie"
dbus-launch --exit-with-session gnome-session
```

---

### Post by JbsTac on 2007-09-09
Thanks Forlong! I'm a complete noob with any Ubuntu, so I just installed XGL as part of "setting up" and had no idea what was going on. Thanks again.:)

---

### Post by ArtF10 on 2007-09-09
One thing I noticed for borders:  If you are not particularly interested in them you can move windows around as USUAL using Alt+Drag window.  If you intend on changing themes every month, then you'll have to try something else because you will most likely need those borders.

**[COLOR="Red"]EDIT[/COLOR]**:  I meant to say "If you are not particularly interested in **themes (AND do not have window borders for whatever reason) **you can ......"

---

### Post by Bart_D on 2007-09-09
Forlong, will you also release a blog for installing Compiz Fusion on Gutsy?  I'm asking because Gutsyis right around the corner.  I'm not sure if it will come with the WHOLE package pre-installed or whether it will contain certain parts only.  In any event, could you post a blog entry for installing CF on Gutsy...it would really help us.  Especially those who used/are using this thread.
Thanks.

---

### Post by GSF1200S on 2007-09-09
Great guide nonetheless, pretty much all of my problems have been resolved.

Hey forlong, can you tell me if this is a bug? For some reason if I try to open a link from an email in kmail, firefox wont open the link. its really weird. Does that problem exist with Evolution email?

Also, itd be nice if I could peel a window back like I could on Beryl; on compiz, it pulls the whole window away instead of peeling the corner.

---

### Post by Forlong on 2007-09-10
> **Bart_D said:**
> Forlong, will you also release a blog for installing Compiz Fusion on Gutsy?  I'm asking because Gutsyis right around the corner.  I'm not sure if it will come with the WHOLE package pre-installed or whether it will contain certain parts only.  In any event, could you post a blog entry for installing CF on Gutsy...it would really help us.  Especially those who used/are using this thread.
Thanks.
Although I guess it won't be really hard to install CF on Gutsy I can do that for you. Sure, why not.

Maybe I will start a new set up guide then as well. Or I'll just update the current one.
One way or another, I will let you know.
> **GSF1200S said:**
> Hey forlong, can you tell me if this is a bug? For some reason if I try to open a link from an email in kmail, firefox wont open the link. its really weird. Does that problem exist with Evolution email?
I'm using Thunderbird and that works fine.

The only thing I can think of right now, is the **Dbus** plugin - is it enabled?
> **GSF1200S said:**
> Also, itd be nice if I could peel a window back like I could on Beryl; on compiz, it pulls the whole window away instead of peeling the corner.
Yeah, I know what you mean... haven't missed that feature, so I don't know about that right now. I remember that you could configure that in *wobbly windows* on Beryl but I can't find anything on Compiz.

But there's kind of a workaround to do that:
Maximise a window, then press [Alt] and yank with the middle mouse button.
([Alt]+[Middle Mousebutton] is actually for resizing)

---

### Post by Bart_D on 2007-09-10
> **Forlong said:**
> Although I guess it won't be really hard to install CF on Gutsy I can do that for you. Sure, why not.

Maybe I will start a new set up guide then as well. Or I'll just update the current one.
One way or another, I will let you know.

Thanks, that would be greatly appreciated.  Maybe post a link to the blog in your signature.

---

### Post by MrWookie on 2007-09-10
> **Forlong said:**
> Could you please post the output of
```
grep -v ^# /etc/X11/xorg.conf
```

Hey, sorry I've been a little slow to respond to this, but here's the xorg.conf file you asked for:

```
Section "ServerLayout"
    Identifier     "Layout0"
    Screen      0  "Screen0" 0 0
    InputDevice    "Keyboard0" "CoreKeyboard"
    InputDevice    "Mouse0" "CorePointer"
EndSection

Section "Files"
    RgbPath         "/usr/X11R6/lib/X11/rgb"
EndSection

Section "Module"
    Load           "dbe"
    Load           "extmod"
    Load           "type1"
    Load           "freetype"
    Load           "glx"
EndSection

Section "ServerFlags"
    Option         "Xinerama" "0"
EndSection

Section "InputDevice"

    # generated from default
    Identifier     "Mouse0"
    Driver         "mouse"
    Option         "Protocol" "auto"
    Option         "Device" "/dev/psaux"
    Option         "Emulate3Buttons" "no"
    Option         "ZAxisMapping" "4 5"
EndSection

Section "InputDevice"

    # generated from default
    Identifier     "Keyboard0"
    Driver         "kbd"
EndSection

Section "Monitor"

    # HorizSync source: edid, VertRefresh source: edid
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "ViewSonic Q20wb"
    HorizSync       30.0 - 82.0
    VertRefresh     56.0 - 75.0
    Option         "DPMS"
EndSection

Section "Device"
    Identifier     "Videocard0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce 7600 GT"
EndSection

Section "Screen"
    Identifier     "Screen0"
    Device         "Videocard0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "TwinView" "1"
    Option         "metamodes" "DFP-0: 1680x1050 +1280+0, DFP-1: nvidia-auto-select +0+0; DFP-0: 1400x1050 +0+0, DFP-1: nvidia-auto-select +1400+0; DFP-0: 1280x1024 +0+0, DFP-1: nvidia-auto-select +1280+0; DFP-0: 1280x960 +0+0, DFP-1: nvidia-auto-select +1280+0; DFP-0: 1152x864 +0+0, DFP-1: nvidia-auto-select +1152+0; DFP-0: 1024x768 +0+0, DFP-1: nvidia-auto-select +1024+0; DFP-0: 800x600 +0+0, DFP-1: nvidia-auto-select +800+0; DFP-0: 640x480 +0+0, DFP-1: nvidia-auto-select +640+0"
    Option         "AddARGBGLXVisuals" "True"
    SubSection     "Display"
        Depth       24
        Modes      "1600x1200" "1280x1024" "1024x768" "800x600" "640x480"
    EndSubSection
EndSection


```

---

### Post by Forlong on 2007-09-10
Sorry, I really don't know about such specific Nvidia options.
Did *you* know what you were doing, when you added them there?

I went back in the thread to find the error message again, that you posted and it said something about *depth 32* but I can't make this out in your xorg.conf
But Compiz obviously has some problems with (at least) one of your settings there.

Maybe you should tell us, what kind of a set up you have. Dual monitor?

---

### Post by pookey on 2007-09-11
Hi, sorry to bring up old problems, but I'm having issues.

I run kubuntu, and I've tried following the guide on [https://help.ubuntu.com/community/CompositeManager/CompizFusion](https://help.ubuntu.com/community/CompositeManager/CompizFusion) , however I had the problem with ' libcompizconfig-backend-kconfig but it is not installable'.  As suggested in this forum, I updated my source list to include

```
deb http://ppa.dogfood.launchpad.net/amaranth/ubuntu feisty main
```

I removed  compiz and compizconfig-settings-manager , which uninstaled a whole load of extra packages.
Now I've tried re-installing, and I see this:

 ```

The following packages have unmet dependencies.
  compiz-kde: Depends: compiz-core (= 1:0.5.2-0ubuntu3~ppa4) but 1:0.5.2+git20070829-0ubuntu1amaranth1 is to be installed
              Depends: compiz-plugins (= 1:0.5.2-0ubuntu3~ppa4) but 1:0.5.2+git20070829-0ubuntu1amaranth1 is to be installed

```

I'm not too sure what I'm doing wrong here - can anyone help?

Thanks,

---

### Post by Forlong on 2007-09-11
> **pookey said:**
> I removed  compiz and compizconfig-settings-manager , which uninstaled a whole load of extra packages.
A whole load but certainly not enough. **compiz** is just a metapackage, if xou remove it, all packages it installed with it are left installed.

That's why you have broken dependencies now. Never mix repositories.


Follow the command to remove compiz _completely_ and install again as described here: [http://forlong.blogage.de/article/2007/8/29/How-to-install-Compiz-Fusion-on-Ubuntu-Feisty---tutorial-for-advanced-andor-KDE-as-well-as-Xfce-users](http://forlong.blogage.de/article/2007/8/29/How-to-install-Compiz-Fusion-on-Ubuntu-Feisty---tutorial-for-advanced-andor-KDE-as-well-as-Xfce-users)

---

### Post by bertlacy on 2007-09-11
WONDERFUL GUIDE, MUCH PROPS!!!!!

I only have one problem, i can't get the 'cube' effect to work.  Followed your guide, might have missed something but everything else works.  I have set the desktop's to 4 and everything else to 1, what gives?

---

### Post by Forlong on 2007-09-12
Please be more specific, what exactly is not working for you?
And did you really follow the instructions, because I said specifically _not_ to increase the numbers of desktops.

---

### Post by tagrace on 2007-09-12
Your guide worked great. Glad to be rid of the "other" installer.

What is up with the version number bug? I've disabled the repository so it won't try to update all the time and that's fine. Will this be fixed or should we just live with it till the REAL stuff comes out with Gutsy.

Thanks for your work on this.

Ted

---

### Post by MrWookie on 2007-09-12
> **Forlong said:**
> Sorry, I really don't know about such specific Nvidia options.
Did *you* know what you were doing, when you added them there?

I went back in the thread to find the error message again, that you posted and it said something about *depth 32* but I can't make this out in your xorg.conf
But Compiz obviously has some problems with (at least) one of your settings there.

Maybe you should tell us, what kind of a set up you have. Dual monitor?

Yeah, I mentioned that earlier, but perhaps not prominently enough.  I have a dual monitor setup using Twin View, as indicated by the line in the conf file     'Option         "TwinView" "1".'  After poking around, I really can't see any significant difference between my setup and the other setups that have gotten this working other than the fact that I'm running TwinView, and in all probability, most other people aren't.  I'm not sophisticated enough w/ Compiz Fusion to know what to do to try and get around this, but I'd suspect it's a good place to start looking.  Is there anyone out there who's gotten CF to work on a dual monitor setup?

I'll have to see about turning off TwinView and then following your guide to see if it'll work.  Unfortunately, though, dual monitors are more important to me than the desktop effects, so even if turning off TwinView does enable CF, I'll end up subsequently disabling CF and reverting back to TwinView.

---

### Post by mban23 on 2007-09-12
Hi all. I'm new to linux and I've installed compiz with this tutorial. However, my panels are the same like they were before installing compiz. Everything else looks like it should, but top and bottom panel (ubuntu feisty, gnome) don't look like they should when I set a theme in emerald. How to fix this?

Thanks.

---

### Post by Schnoidz on 2007-09-12
> **orange2k said:**
> I followed this guide, and let me tell you: this is the best ******* guide for installing compiz fusion that Ive seen so far. For the first time since I started using compiz (or beryl for that matter), can I say that Ive experienced no troubles or errors. No more constant searching and asking unneccessary questions on the forum for me...

I think this guide of yours deserves a special place in the forum, as the best/most-easy-to-use for newbies such as myself...

It should become a sticky...

One more time: this kicks major ***...:)

It worked perfectly for me too.  I used it on my laptop with Intel graphics yesterday and on a P4 2.2 desktop with an old ATI card tonight.  No problems on either system!

---

### Post by Forlong on 2007-09-13
> **tagrace said:**
> What is up with the version number bug? I've disabled the repository so it won't try to update all the time and that's fine. Will this be fixed or should we just live with it till the REAL stuff comes out with Gutsy.
As far as I know, we unfortunately have to live with this until Gutsy comes out.
> **mban23 said:**
> Hi all. I'm new to linux and I've installed compiz with this tutorial. However, my panels are the same like they were before installing compiz. Everything else looks like it should, but top and bottom panel (ubuntu feisty, gnome) don't look like they should when I set a theme in emerald. How to fix this?
What do you mean they "don't look like they should"?
Emerald is only a window decorator - that means it's responsible for the titlebars of your windows and nothing else.


@MrWookie: sorry, I have no experiences with dual monitor setpups. You might want to start a new thread (or search for existing ones).

---

### Post by techstop on 2007-09-13
> **MrWookie said:**
>  Is there anyone out there who's gotten CF to work on a dual monitor setup?

Yes, it's working fine here on dual monitors. They are set up as independent desktops, and I get window decorations on both monitors. 

I posted a little script here that got it working properly for me;

[http://ubuntuforums.org/showthread.php?t=544145](http://ubuntuforums.org/showthread.php?t=544145)

---

### Post by ArtF10 on 2007-09-13
Yup, agreed with the top of the page.  This should be a sticky.

---

### Post by mban23 on 2007-09-14
> **Forlong said:**
> What do you mean they "don't look like they should"?
Emerald is only a window decorator - that means it's responsible for the titlebars of your windows and nothing else.

I figured it out, apparently. Anyway, thanks for your reply.

---

### Post by Bart_D on 2007-09-14
Forlong, I had mentioned earlier in the thread that it would be great if you could write a blog for Gutsy as well.  Well, it appears that Gutsy will have automatic determination of whether or not one's system can handle CF...if YEs, it will run CF, if not it """won't''' I think.  Atleast that's the way I understand it.  I read this in one of the threads in the "Community Cafe" section.  I would still prefer a blog entry to reassure me....but I don;'t know what, if anything, would be included if it's all ALREADY pre-installed....

---

### Post by jpyanowski on 2007-09-14
Wonderful How-To.   ):P I now have Compiz with Emerald themes and I am happy. :) Your blog shows how much time you put into it. It's been said before...good work.

---

### Post by guardian653 on 2007-09-16
is it just me or has kde support disappeared using the repo in this guide?
apt complains that libcompizconfig-backend-kconfig is not installable (its nowhere to be found...)

will just emerald for the moment...

---

### Post by Forlong on 2007-09-16
> **guardian653 said:**
> is it just me or has kde support disappeared using the repo in this guide?
Did you follow [this guide](http://forlong.blogage.de/article/2007/8/29/How-to-install-Compiz-Fusion-on-Ubuntu-Feisty---tutorial-for-advanced-andor-KDE-as-well-as-Xfce-users) for KDE?
It uses the "old" repository, as the updated one (from the main how-to) is known not to include the package you mentioned.
I will check later in the day if it's still OK to use (I will have to reboot into another install for that).


@Bart_D: I'm going to provide a how-to for Gutsy when the time is right. Definitely not before the Beta release. I don't want people to upgrade their system just because it seems easier to install Compiz Fuison then.

As for your concerns: I wanted to write an article about the decision of Compiz being the default window manager of Gutsy but my wife got sick and the article is on hold atm. I will let you know when it's finally up.


Thanks again for all of your nice comments. I really appreciate it because I did put a lot of time and effort into this.

---

### Post by Forlong on 2007-09-16
OK, guardian653, I checked and the repository from the alternative how-to should work just fine.

Make sure you have
```
deb http://ppa.dogfood.launchpad.net/amaranth/ubuntu feisty main
```
included in your sources list and _not_
```
deb http://ppa.launchpad.net/amaranth/ubuntu feisty main
```

---

### Post by Porpoise on 2007-09-16
Well guys & Forlong

I've been playing around with this for hours now but I have got one small step forward. Somehow, I now have an extra mode (still not the 1680x1050 it should be but it's still better than it was) 1280x768. I haven a clue where that mode has suddenly just come from as it's not in my xorg.conf!?!

```


Section "Files"
	FontPath	"/usr/share/fonts/X11/misc"
	FontPath	"/usr/share/fonts/X11/cyrillic"
	FontPath	"/usr/share/fonts/X11/100dpi/:unscaled"
	FontPath	"/usr/share/fonts/X11/75dpi/:unscaled"
	FontPath	"/usr/share/fonts/X11/Type1"
	FontPath	"/usr/share/fonts/X11/100dpi"
	FontPath	"/usr/share/fonts/X11/75dpi"
	# path to defoma fonts
	FontPath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
	Load	"i2c"
	Load	"bitmap"
	Load	"ddc"
	Load	"dri"
	Load	"extmod"
	Load	"freetype"
	Load	"glx"
	Load	"int10"
	Load	"vbe"
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"us"
	Option		"XkbVariant"	"intl"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"		"/dev/input/mice"
	Option		"Protocol"		"ImPS/2"
	Option		"ZAxisMapping"		"4 5"
	Option		"Emulate3Buttons"	"true"
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"stylus"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"		"stylus"
	Option		"ForceDevice"	"ISDV4"		# Tablet PC ONLY
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"eraser"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"		"eraser"
	Option		"ForceDevice"	"ISDV4"		# Tablet PC ONLY
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"cursor"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"		"cursor"
	Option		"ForceDevice"	"ISDV4"		# Tablet PC ONLY
EndSection

Section "Device"
	Identifier	"ATI Technologies Inc Radeon RV200 QW [Radeon 7500]"
	Driver		"ati"
	BusID		"PCI:1:0:0"
EndSection

Section "Monitor"
	Identifier	"SyncMaster"
	ModelName	"SyncMaster 225MW"
	HorizSync	28-51
	VertRefresh	43-60
	Option "dpms"
	
EndSection



Section "Screen"
	Identifier	"Default Screen"
	Device		"ATI Technologies Inc Radeon RV200 QW [Radeon 7500]"
	Monitor		"SyncMaster"
	DefaultDepth	24
	SubSection "Display"
		Depth		24
		Modes		"1680x1050" "1280X1024" "1024X768" "800X600"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
	InputDevice     "stylus"	"SendCoreEvents"
	InputDevice     "cursor"	"SendCoreEvents"
	InputDevice     "eraser"	"SendCoreEvents"
EndSection

Section "DRI"
	Mode	0666
EndSection

```

and here is the output from xrandr:

```

 SZ:    Pixels          Physical       Refresh
 0   1280 x 800    ( 485mm x 303mm )   60
*1   1280 x 768    ( 485mm x 303mm )  *60
 2   1152 x 768    ( 485mm x 303mm )   55
 3   1024 x 768    ( 485mm x 303mm )   60
 4    800 x 600    ( 485mm x 303mm )   60   56
 5    640 x 480    ( 485mm x 303mm )   60
 6    400 x 300    ( 485mm x 303mm )   60
Current rotation - normal
Current reflection - none
Rotations possible - normal
Reflections possible - none
steve@Bigrock:~$ sudo gedit /etc/X11/xorg.conf
Launching a SCIM daemon with Socket FrontEnd...
Loading simple Config module ...
Creating backend ...
Loading socket FrontEnd module ...
Starting SCIM as daemon ...
GTK Panel of SCIM 1.4.4


```

I don understand how we can have one thing in xorg.conf and something entirely different from xrandr......?????

Is there some configuration file somewhere else that the system is picking up data from?

It's really frustrating, as I would really like to run the screen at it's native resolution.:confused:

---

### Post by Forlong on 2007-09-17
Hello Porpoise,

your problem is not related to Compiz, so this not the best thread to address this, but let's see if we can help you anyway.

First I recommend (re)configuring your xorg.conf
In order to do so, first make a backup:
```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.bak
```
Then run this:
```
sudo dpkg-reconfigure xserver-xorg
```
Set everything as accurate as you can. Look for your monitor's manual first.


If this doesn't help you, you'll have to use modelines, I guess.

---

### Post by DAE_JA_VOO on 2007-09-17
Hi there everyone. I've got a problem :(

Okay here's some background. I installed Ubuntu about 10 days ago for the first time. After installing it, i used this guide to install and configure Compiz and it worked, beautifully, and then i ran into some trouble (irrelevant) and i needed to format and reinstall ubuntu. I did that, and then i followed this guide again, but now, Compiz just doesn't work. I can run it (compiz --replace) and even edit stuff in the config panel, but none of the effects actually WORK.

Any suggestions?

---

### Post by Porpoise on 2007-09-17
> **Forlong said:**
> Hello Porpoise,

your problem is not related to Compiz, so this not the best thread to address this, but let's see if we can help you anyway.

First I recommend (re)configuring your xorg.conf
In order to do so, first make a backup:
```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.bak
```
Then run this:
```
sudo dpkg-reconfigure xserver-xorg
```
Set everything as accurate as you can. Look for your monitor's manual first.


If this doesn't help you, you'll have to use modelines, I guess.

You're my man!  :guitar:

I owe you a pint (or quart, or gallon - whatever takes your fancy).

Next job is to get my HP printer on PS101 working!!!

---

### Post by Forlong on 2007-09-18
> **DAE_JA_VOO said:**
> I can run it (compiz --replace) and even edit stuff in the config panel, but none of the effects actually WORK.
Could you please post the output of
```
compiz --replace
```
in the terminal?

---

### Post by envykris on 2007-09-18
Hi..
I've been trying for 2 days now on my T21, Feisty with Savage card.
Direct Rendering : YES
GLX installed and gives around 360 FPS.
When i try compiz -- replace, i get the following output:

```

compiz --replace
Checking for Xgl: not present. 
Checking for texture_from_pixmap: not present. 
Trying again with indirect rendering:
Checking for texture_from_pixmap: present. 
Checking for non power of two support: Not present. 
aborting and using fallback: /usr/bin/metacity 
Window manager warning: "" found in configuration database is not a valid value for keybinding "toggle_shaded"

```

Can somebody help me on this?
cheers!
PS: I installed Compiz fusion exactly as in Forlong's URL.

---

### Post by Forlong on 2007-09-18
Sorry, I have no experience with Savage cards at all. I'd recommend starting a separate thread for that.

---

### Post by DAE_JA_VOO on 2007-09-18
> **Forlong said:**
> Could you please post the output of
```
compiz --replace
```
in the terminal?

Here you go :)

```
Checking for Xgl: not present. 
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
Checking for nVidia: present. 
Checking for Xgl: not present. 

(gtk-window-decorator:7175): Wnck-WARNING **: Unhandled action type (nil)

(gtk-window-decorator:7175): Wnck-WARNING **: Unhandled action type (nil)

(gtk-window-decorator:7175): Wnck-WARNING **: Unhandled action type (nil)

(gtk-window-decorator:7175): Wnck-WARNING **: Unhandled action type (nil)

(gtk-window-decorator:7175): Wnck-WARNING **: Unhandled action type (nil)

(gtk-window-decorator:7175): Wnck-WARNING **: Unhandled action type (nil)

(gtk-window-decorator:7175): Wnck-WARNING **: Unhandled action type (nil)

(gtk-window-decorator:7175): Wnck-WARNING **: Unhandled action type (nil)
/usr/bin/compiz.real (video) - Warn: No 8 bit GLX pixmap format, disabling YV12 image format
Segmentation fault (core dumped)

```

I don't understand.... i did the EXACT same procedure as last time, but this time it doesn't work :?

---

### Post by Forlong on 2007-09-18
> **DAE_JA_VOO said:**
> ```
Segmentation fault (core dumped)
```
Wow, that's new :)
There's really no error message besides that :?

Please post the output of
```
dpkg -l | grep compiz
```

---

### Post by DAE_JA_VOO on 2007-09-18
> **Forlong said:**
> Please post the output of
```
dpkg -l | grep compiz
```

Here you go :)

```
ii  compiz                                     0.5.2+git20070829-0ubuntu1amaranth1    OpenGL window and compositing manager
ii  compiz-core                                0.5.2+git20070829-0ubuntu1amaranth1    OpenGL window and compositing manager
ii  compiz-fusion-plugins-extra                0.5.2+git20070829-0ubuntu1~ppa1        Collection of extra plugins from OpenComposi
ii  compiz-fusion-plugins-main                 0.5.2+git20070829-0ubuntu1~ppa1        Collection of plugins from OpenCompositing f
ii  compiz-gnome                               0.5.2+git20070829-0ubuntu1amaranth1    OpenGL window and compositing manager - GNOM
rc  compiz-gtk                                 0.3.6-1ubuntu13                        OpenGL window and compositing manager - Gtk 
ii  compiz-plugins                             0.5.2+git20070829-0ubuntu1amaranth1    OpenGL window and compositing manager - plug
ii  compizconfig-settings-manager              0.5.2+git20070829-0ubuntu1~ppa1        Compiz configuration settings manager
ii  emerald                                    0.3~git20070717-0ubuntu1~ppa1          Decorator for compiz-fusion
ii  libcompizconfig-backend-gconf              0.5.2+git20070829-0ubuntu1~ppa1        Settings library for plugins - OpenCompositi
ii  libcompizconfig0                           0.5.2+git20070829-0ubuntu1~ppa1        Settings library for plugins - OpenCompositi
ii  libemeraldengine0                          0.3~git20070717-0ubuntu1~ppa1          Decoration engines for compiz-fusion
ii  python-compizconfig                        0.5.2+git20070829-0ubuntu1~ppa1        Compiz configuration system bindings

```

---

### Post by Forlong on 2007-09-18
Looks fine to me apart from the configurations from compiz-gtk
Try this to remove them:
```
sudo dpkg --purge compiz-gtk
```
(I'm not 100% sure about the command and I can't test it, because I don't have any configurations from removed packages right now - so please let me know, if this step didn't work for you)

Other than that I can only give you the advice to go to CCSM and open the Preferences. There you switch to Gconf and click "Reset to defaults".
Then switch back to Flat-file, choose the Default profile and do the same (and stick to this backend!)

Afterwards try to run *compiz --replace* again.

---

### Post by DAE_JA_VOO on 2007-09-18
> **Forlong said:**
> Looks fine to me apart from the configurations from compiz-gtk
Try this to remove them:
```
sudo dpkg --purge compiz-gtk
```
(I'm not 100% sure about the command and I can't test it, because I don't have any configurations from removed packages right now - so please let me know, if this step didn't work for you)

Other than that I can only give you the advice to go to CCSM and open the Preferences. There you switch to Gconf and click "Reset to defaults".
Then switch back to Flat-file, choose the Default profile and do the same (and stick to this backend!)

Afterwards try to run *compiz --replace* again.

I did all of that, same problem :(

---

### Post by Forlong on 2007-09-18
Sorry, I have to trust you on what you say (that you installed everything like last time, when it worked for you) and the error message about the dumped core just isn't of any help.

So right now... I'm lost. There has to be *something* you did differently but only you can know that.

Unfortunately there is no trace of what can be the problem... so let's sort things out:
[list][*]totally temove Compiz.
[*]disable the repository for Compiz Fusion (and reload the package informations)
[*]install **desktop-effects** (from the Ubuntu repositories)[/list]
Then start
```
compiz --replace
```
and see if it wiorks - if so, we know at least it has something to do with the packages.

---

### Post by DAE_JA_VOO on 2007-09-19
Don't worry dude, i managed to get my hands on a copy of ubuntu Ultimate and i just installed that instead. So now Compiz is working fine again :)

Thanks for your help though :D

---

### Post by Jadephyre on 2007-09-19
Compiz Fusion runs great :)

Not really as smooth as i'd like it to, but i see great things regarding performance on the older cards with the OpenSource Radeon Driver after AMD released some vital Info about their chips.

I'm running it on Radeon 9600 backed by an AthlonXP 3000+ and 1 Gigabyte DDR400 RAM.
Hopefully this how-to will also work on my Laptop by the time the Official 8.42 Radeon Binary Driver supporting AIGLX will be released :)
On another note: I just ticked off a Buddy of mine two days ago when i showed him what was possible with Compiz Fusion and the only thing he said was "Vista could do that too, if they would include it".
He so stubbornly refuses to believe that Microhell just uses him and every other Vista User as a Betatester that it's not even funny anymore.

Unfortunately i guess even i will have to upgrade my XP to Vista once Games will refuse to even install on XP... Halo 2 was the first sour taste of that future...

---

### Post by Forlong on 2007-09-19
> **Jadephyre said:**
> I'm running it on Radeon 9600 backed by an AthlonXP 3000+ and 1 Gigabyte DDR400 RAM.
Well, then you're better off than me: Athlon XP 2800+ with 512 MB RAM and a Radeon 9600 (XT though).
And you are complaining it's not smooth enough for you? [-X 

:)

---

### Post by kevdog on 2007-09-20
Furlong

Thanks for hanging in there an answering my question on your website.  Maybe I can provide more info to help you

Using Intel graphics card:
```
sudarshan@Sudarshan:/etc/X11$ lsmod | grep 915
i915                   25472  2 
drm                    81044  3 i915
```

I have not to my knowledge installed xgl (I know this for certain) or aiglx.  I would prefer aiglx since Im running a laptop with intel card.

Here is my xorg.conf file (I fixed it, and at least with the fixes Im not losing any more tops -- this is per links in this forum):
```

Section "Files"
        FontPath        "/usr/share/fonts/X11/misc"
        FontPath        "/usr/share/fonts/X11/cyrillic"
        FontPath        "/usr/share/fonts/X11/100dpi/:unscaled"
        FontPath        "/usr/share/fonts/X11/75dpi/:unscaled"
        FontPath        "/usr/share/fonts/X11/Type1"
        FontPath        "/usr/share/fonts/X11/100dpi"
        FontPath        "/usr/share/fonts/X11/75dpi"
        # path to defoma fonts
        FontPath        "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
        Load    "i2c"
        Load    "bitmap"
        Load    "ddc"
        Load    "dri"
        Load    "extmod"
        Load    "freetype"
        Load    "glx"
        Load    "int10"
        Load    "vbe"
        Load    "dbe"
        Load    "init10"
        Load    "type1"
EndSection

Section "InputDevice"
        Identifier      "Generic Keyboard"
        Driver          "kbd"
        Option          "CoreKeyboard"
        Option          "XkbRules"      "xorg"
        Option          "XkbModel"      "pc105"
        Option          "XkbLayout"     "us"
EndSection

Section "InputDevice"
        Identifier      "Configured Mouse"
        Driver          "mouse"
        Option          "CorePointer"
        Option          "Device"                "/dev/input/mice"
        Option          "Protocol"              "ImPS/2"
        Option          "ZAxisMapping"          "4 5"
        Option          "Emulate3Buttons"       "true"
EndSection

Section "InputDevice"
        Identifier      "Synaptics Touchpad"
        Driver          "synaptics"
        Option          "SendCoreEvents"        "true"
        Option          "Device"                "/dev/psaux"
        Option          "Protocol"              "auto-dev"
        Option          "HorizScrollDelta"      "0"
EndSection

Section "InputDevice"
        Driver          "wacom"
        Identifier      "stylus"
        Option          "Device"        "/dev/input/wacom"
        Option          "Type"          "stylus"
        Option          "ForceDevice"   "ISDV4"         # Tablet PC ONLY
EndSection

Section "InputDevice"
        Driver          "wacom"
        Identifier      "eraser"
        Option          "Device"        "/dev/input/wacom"
        Option          "Type"          "eraser"
        Option          "ForceDevice"   "ISDV4"         # Tablet PC ONLY
EndSection

Section "InputDevice"
        Driver          "wacom"
        Identifier      "cursor"
        Option          "Device"        "/dev/input/wacom"
        Option          "Type"          "cursor"
        Option          "ForceDevice"   "ISDV4"         # Tablet PC ONLY
EndSection

Section "Device"
        Identifier      "Intel Corporation 82830 CGC [Chipset Graphics Controller]"
        Driver          "i810"
        BusID           "PCI:0:2:0"
        Option          "XAANoOffscreenPixmaps" "true"
        #Option         "DRI"   "true"
EndSection

Section "Monitor"
        Identifier      "Generic Monitor"
        Option          "DPMS"
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Device          "Intel Corporation 82830 CGC [Chipset Graphics Controller]"
        Monitor         "Generic Monitor"
        DefaultDepth    24
        SubSection "Display"
                Depth           1
                Modes           "1024x768"
        EndSubSection
        SubSection "Display"
                Depth           4
                Modes           "1024x768"
        EndSubSection
        SubSection "Display"
                Depth           8
                Modes           "1024x768"
        EndSubSection
        SubSection "Display"
                Depth           15
                Modes           "1024x768"
        EndSubSection
        SubSection "Display"
                Depth           16
                Modes           "1024x768"
        EndSubSection
        SubSection "Display"
                Depth           24
                Modes           "1024x768"
        EndSubSection
EndSection

Section "ServerLayout"
        Identifier      "Default Layout"
        Screen          "Default Screen"
        InputDevice     "Generic Keyboard"
        InputDevice     "Configured Mouse"
        InputDevice     "stylus"        "SendCoreEvents"
        InputDevice     "cursor"        "SendCoreEvents"
        InputDevice     "eraser"        "SendCoreEvents"
        InputDevice     "Synaptics Touchpad"
        #Option         "AIGLX" "true"
EndSection

Section "DRI"
        #Group  "video"
        Mode    0666
EndSection

Section "Extensions"
        Option  "Composite"     "Enable"
EndSection

```

Im noticing the section under "Device" list i810 when the i915 driver is loaded does this matter??

Anyway I installed as per your guide (I was very careful doing this)
When I run compiz --replace from command line this is what I get:

```
sudarshan@Sudarshan:/etc/X11$ compiz --replace
Checking for Xgl: not present. 
Checking for texture_from_pixmap: not present. 
Trying again with indirect rendering:
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
Checking for nVidia: not present. 
Checking for Xgl: not present. 

(gtk-window-decorator:5894): Wnck-WARNING **: Unhandled action type (nil)

(gtk-window-decorator:5894): Wnck-WARNING **: Unhandled action type (nil)

(gtk-window-decorator:5894): Wnck-WARNING **: Unhandled action type (nil)

(gtk-window-decorator:5894): Wnck-WARNING **: Unhandled action type (nil)

(gtk-window-decorator:5894): Wnck-WARNING **: Unhandled action type (nil)

(gtk-window-decorator:5894): Wnck-WARNING **: Unhandled action type (nil)

(gtk-window-decorator:5894): Wnck-WARNING **: Unhandled action type (nil)

(gtk-window-decorator:5894): Wnck-WARNING **: Unhandled action type (nil)

(gtk-window-decorator:5894): Wnck-WARNING **: Unhandled action type (nil)

(gtk-window-decorator:5894): Wnck-WARNING **: Unhandled action type (nil)

(gtk-window-decorator:5894): Wnck-WARNING **: Unhandled action type (nil)

(gtk-window-decorator:5894): Wnck-WARNING **: Unhandled action type (nil)
/bin/sh: gtk-window-manager: not found
/usr/bin/compiz.real: symbol lookup error: /usr/lib/compiz/libdecoration.so: undefined symbol: decor_apply_gravity
Window manager warning: "" found in configuration database is not a valid value for keybinding "toggle_shaded"

```

Could you point me in the right direction?? Thanks  Seems like I havent installed something!

---

### Post by Forlong on 2007-09-20
> ```
/usr/bin/compiz.real: symbol lookup error: /usr/lib/compiz/libdecoration.so: undefined symbol: decor_apply_gravity
```

Enable the repository again and run
```
sudo apt-get update && sudo apt-get upgrade
```
and install any packages provided for upgrade - especially **libdecoration0**

---

### Post by kevdog on 2007-09-20
That worked!!!

Now how do I get the cube???

---

### Post by Forlong on 2007-09-20
> **kevdog said:**
> Now how do I get the cube???
[How to set up Compiz Fusion](http://forlong.blogage.de/article/2007/8/29/How-to-set-up-Compiz-Fusion) &#8594; Getting the cube

---

### Post by kevdog on 2007-09-20
I was able to get all the other plugins mentioned on your blog, however this cube thing is driving me up the wall.

I think I did everything right, but Im gettting no top or bottom of cube, and even though it is rotating, all Im getting on my screen is one side rotating to the next.  (Im getting nothing that resembles a smaller cube in the middle of the screen).  I have cube cabs, rotate cube, desktop cube, cube reflection enabled, but I must be doing something wrong.

---

### Post by Forlong on 2007-09-20
> **kevdog said:**
> I think I did everything right, but Im gettting no top or bottom of cube,
You mean you don't have any images on top and bottom? That's taken care of by the *Cube Cabs* plugin. I'm not sure if I get what you want there...
> **kevdog said:**
> and even though it is rotating, all Im getting on my screen is one side rotating to the next.  (Im getting nothing that resembles a smaller cube in the middle of the screen).
Again, I'm not quote sure if I understand what you mean. Try changing *Zoom* in the Rotate Cube plugin

---

### Post by Vandread on 2007-09-20
Oh wow I get to thank the man who created that tutorial? 

Just wanted to say thank you, your instructions were very detailed and easy to understand. I am brand new to ubuntu and the linux world and was interested in getting this to run. I saw a video of compiz and was floored, also DL.TV couldnt stop talking about ubuntu so i took the plunge. Just wanted to say even a beginner like me could get this working and you have made my ubuntu experience exciting. 

I greatly appreciate the time and effort you took to make that guide.:KS

---

### Post by kevdog on 2007-09-20
See next post

---

### Post by kevdog on 2007-09-20
Ive done a bunch of changing of the settings, but its like I dont see any effects.

I guess Im going to have to spell it out (not top or bottom of cube is seen, its purely a 2D output Im getting):

```
Desktop Cube: General Mipmap Automatic
                         Appearance
                                    Cube Color Green
                                    Background Image Blank
                                    Cube Caps
                                         Scale Image
                                         /usr/share/gdm/themes/Human/ubuntu.png
                                        Adjust image
                                     Skydome
                                          Skydome
                                          Skydome Image Blank
                                          Animate Skydome
                         Behaivor
                                    Inside Cube (option checked)
                                    Acc=1
                                    Speed=1.5
                                    Timestep=1.2
                         Transparent Cube
                                    Opacity During Rotation 66
                                    Opacity when not Rotating 100
                                    Fade Time 1.0
                                    Transparency Only on Mouse Rotate (not checked)
                          General
                                      Unfold Cnt-alt-down
                                      Next slide space
                                     Prev Slide disabled

Rotate Cube
      General
              Edge Flip Pointer Enabled
             Edge Flip Move Enabled
               Edge Flip Dnd Enabled
              Flip Time = 350
              Raise on Rotate Enabled
              Pointer Invert Y Disabled
              Pointer Sensitity = 1.0
             Accerlation=4.0
              Snap to Top Face = Disabled
              Speed = 2
              Timestep = 1.0
              Zoom = 0.5
      Actions
               Initiate Disabled cntl-alt-button1
               Rotate Left
               Rotate Right
              Rotate Left with Window
               Rotate Right with Window

Cube Caps
    Appearance
           Cube Top Color = Orange
           Cube Bottom color = Brown
           Top Image = fusioncap.png
           Bottom Image Files = Compizcap.png
    Behaivor
            All options are checked
    Actions
            Next top image Space
            Rest disabled
```


Thats all my options

---

### Post by Forlong on 2007-09-20
> **kevdog said:**
> not top or bottom of cube is seen, its purely a 2D output Im getting
And you really followed all the steps in "Getting the cube"?

Especially this one:
> Secondly, we have to increase the number of the virtual desktops to **4**
at **General Options &#8594; Desktop Size &#8594; Horizontal Virtual Size**
(the other two options have to be left at **1**)

---

### Post by Bigdeath on 2007-09-20
I had it working for a while then I changed my xorg.conf and it stopped working. Emerald never worked with it. Now I get no borders no matter what windows decorator I use. So I just went back to beryl.

---

### Post by Forlong on 2007-09-20
So... are you looking for help or is that just a statement? :-k

---

### Post by Bigdeath on 2007-09-20
I been playing with compiz off and on all day. No matter what I can't get emerald to work with it. And If I update beryl or emerald from the amaranth or trevino repos it breaks them. What would cause that?

Oh and btw this tut is pretty good. At least got compiz working just can't use emerald with it.

[http://kevin.vanzonneveld.net/techblog/article/enable_compizfusion_in_ubuntu_feisty/](http://kevin.vanzonneveld.net/techblog/article/enable_compizfusion_in_ubuntu_feisty/)

---

### Post by kevdog on 2007-09-20
See next post - sorry

---

### Post by kevdog on 2007-09-20
Sorry I did forget to include the options when I wrote the original settings (but this is what I had for the settings):

```
General Options
    General
         Audible Bell = Enabled
         Hide Skip Taskbar Windows = Enabled
         Ignore Hints When Maximized = Enabled
         Terminal Command line = gnome-terminial
         Cusor Theme Blank
         Cursor Size = 18
         Ping Delay = 5000
         Unredirect Fullscreen Windows = Disabled
         Default Icon = icon
    Commands
          All Blank
    Desktop Size
         Horizontal Virtual Size = 4
         Vertical Virtual Size =1
         Number of Desktops =1 
    Display Settings
          Texture Filter = Good
          Detect Refresh Rate = Enabled
          Lighting = Enabled
          Refresh Rate = 50
          Sync to Vblank = Enabled
          Detect Outputs = Enabled
          Outputs = 640x480+0+0
      Focus and Raise Behaviou
          Click to Focus = Enabled
          Auto Raise = Enabled
          Auto Raise Delay = 1000
          Raise on Click = Enabled
          Focus Prevention Windows = any
       Opacity
             Opacity Step = 10
             Everything Else = Blank
             Actions -----> Didnt change any of the defaults
```

Still all the same

---

### Post by Forlong on 2007-09-21
@Bigdeath: please don't link any guides here that make use of Treviño's repository, because the whole point of making this was to prevent people from using it!
Just have a look around the forums and look at every thread that say e.g. "latest update broke my Compiz" - it's all about this repository.

If you want me to help you out, fine. But then you have to follow my How-To step-by-step and tell me, what exactly is not working for you.


@kevdog: How about this... show me your flat-file config instead (I hope you did switch to Flat-file Backend) - it's located here: **~/.config/compiz/compizconfig**

---

### Post by kevdog on 2007-09-21
Furlong

I had to include it as an attachment -- it was too long to cut and paste.  Sorry

---

### Post by Forlong on 2007-09-21
Oh, you sure like to fiddle with those settings, don't you? :)

Let's do it this way: I'm going to boot later in the day into the install I tested the How-To on. Then I'm going to upload my flat-file.ini and you can try if everything works with that one, OK?

---

### Post by Decline- on 2007-09-21
Hi Forlong, thanks for helping me. Now CF works! What I did was enter some GIT folders I had extracted and compiled some while ago, and do make uninstall. Probably some stuff was left behind since that. And then I reinstalled the Amaranth packages. Works!

However, I have some problems. CompizConfig Settings Manager seems to reset every time I login! Tried making a profile, it solved some of it, but not everything (how many cube faces etc.). And I have to enable window decorations, and enable emerald (with fusion-icon). Any tips?

---

### Post by Sammm_ on 2007-09-21
I made my own thread but I should of really posted here...

I followed your xubuntu guide and got this error:

> sam@xubuntu:~$ compiz --replace
Checking for Xgl: present.
Checking for nVidia: not present.
Checking for Xgl: present.
/usr/bin/compiz.real (core) - Error: Could not acquire compositing manager selection on screen 0 display "localhost:1.0"
/usr/bin/compiz.real (core) - Fatal: No manageable screens found on display localhost:1.0
exec: 244: /usr/bin/metacity: not found

Then I loose all my Window Decorations and have to start xfwm4 again. Any idea what's going on?

---

### Post by Forlong on 2007-09-21
> **Decline- said:**
> However, I have some problems. CompizConfig Settings Manager seems to reset every time I login! Tried making a profile, it solved some of it, but not everything (how many cube faces etc.). And I have to enable window decorations, and enable emerald (with fusion-icon). Any tips?
Did you switch to the Flat-file Backend?
And I don't know if those packages work well with fusion-icon (haven't tested).


@Sammm_: how did you set up Xgl?
Did you try the command from the troubleshooting section about Xgl eating too much resources?

---

### Post by Sammm_ on 2007-09-21
> **Forlong said:**
> @Sammm_: how did you set up Xgl?
Did you try the command from the troubleshooting section about Xgl eating too much resources?

I set up XGL using these instructions [https://help.ubuntu.com/community/CompositeManager/Xgl](https://help.ubuntu.com/community/CompositeManager/Xgl)
I'll try that command and get back to you.

---

### Post by Forlong on 2007-09-21
> **Sammm_ said:**
> I set up XGL using these instructions [https://help.ubuntu.com/community/CompositeManager/Xgl](https://help.ubuntu.com/community/CompositeManager/Xgl)
Using *Method A*?

---

### Post by Sammm_ on 2007-09-21
Yes, I used Method A.

Trying that command resulted in the following error...

> sam@xubuntu:~$ LD_PRELOAD=/usr/lib/fglrx/libGL.so.1.2.xlibmesa compiz --replace
ERROR: ld.so: object '/usr/lib/fglrx/libGL.so.1.2.xlibmesa' from LD_PRELOAD cannot be preloaded: ignored.
Checking for Xgl: ERROR: ld.so: object '/usr/lib/fglrx/libGL.so.1.2.xlibmesa' from LD_PRELOAD cannot be preloaded: ignored.
ERROR: ld.so: object '/usr/lib/fglrx/libGL.so.1.2.xlibmesa' from LD_PRELOAD cannot be preloaded: ignored.
present. 
Checking for nVidia: ERROR: ld.so: object '/usr/lib/fglrx/libGL.so.1.2.xlibmesa' from LD_PRELOAD cannot be preloaded: ignored.
ERROR: ld.so: object '/usr/lib/fglrx/libGL.so.1.2.xlibmesa' from LD_PRELOAD cannot be preloaded: ignored.
not present. 
Checking for Xgl: ERROR: ld.so: object '/usr/lib/fglrx/libGL.so.1.2.xlibmesa' from LD_PRELOAD cannot be preloaded: ignored.
ERROR: ld.so: object '/usr/lib/fglrx/libGL.so.1.2.xlibmesa' from LD_PRELOAD cannot be preloaded: ignored.
present. 
ERROR: ld.so: object '/usr/lib/fglrx/libGL.so.1.2.xlibmesa' from LD_PRELOAD cannot be preloaded: ignored.
/usr/bin/compiz.real (core) - Error: Could not acquire compositing manager selection on screen 0 display "localhost:1.0"
/usr/bin/compiz.real (core) - Fatal: No manageable screens found on display localhost:1.0
exec: 244: /usr/bin/metacity: not found


---

### Post by Forlong on 2007-09-21
> **Sammm_ said:**
> Trying that command resulted in the following error...
What's the output of ```
fglrxinfo
```

---

### Post by Decline- on 2007-09-21
> **Forlong said:**
> Did you switch to the Flat-file Backend?
And I don't know if those packages work well with fusion-icon (haven't tested).


Hey never mind, I just installed treviños repo successfully, and there seems to be no problems! And better updated effects (unsupported etc.) :) :)

---

### Post by Sammm_ on 2007-09-21
> **Forlong said:**
> What's the output of ```
fglrxinfo
```

sam@xubuntu:~$ fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: Tungsten Graphics, Inc
OpenGL renderer string: Mesa DRI Intel(R) 915GM 20061017 x86/MMX/SSE2
OpenGL version string: 1.3 Mesa 6.5.2

---

### Post by Forlong on 2007-09-21
And what's saying:
```
lspci | grep VGA
```

---

### Post by Sammm_ on 2007-09-21
> **Forlong said:**
> And what's saying:
```
lspci | grep VGA
```

sam@xubuntu:~$ lspci | grep VGA
00:02.0 VGA compatible controller: Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller (rev 03)

---

### Post by Forlong on 2007-09-21
You shouldn't need Xgl with an intel chip.
Did you try running Compiz without Xgl?

If it doesn't work, take a look at this: [http://wiki.compiz-fusion.org/Intel_with_AiGLX](http://wiki.compiz-fusion.org/Intel_with_AiGLX)

And remove **xorg-driver-fglrx** first, if you have it installed.

---

### Post by Forlong on 2007-09-21
@kevdog: I couldn't upload the file here, so I added it to the very end of the How-To.
Just save it to ~/.config/compiz/compizconfig and you should be able to access it in the preferences of ccsm afterwards.

---

### Post by Sammm_ on 2007-09-21
I made the noob error of editing my xorg file without backing it up, killing my xserver. 
Reinstall time! I'll try it without Xgl and then I'll back up my Xorg server and make some changes, wish me luck! :)

---

### Post by kevdog on 2007-09-21
Furlong

Lets just start with the basics -- I loaded your file and there is no difference for me.

Let me just ask a basic question.  How do you start the cube??? The only thing I am doing is hitting
cnt-alt-<right or left> arrow.  This will definitely spin the desktop to the next virtual desktop, but in only a 2D fashion.  I dont see any top or bottom when I do this.

I can also do cntl-alt-<down arrow>, but this then just gives me a "filmstrip" with 3 of the desktops appearing side by side on the middle of the screen.

Am I missing a key combination to start the cube??

---

### Post by Forlong on 2007-09-21
> **kevdog said:**
> Am I missing a key combination to start the cube??
From the guide:
> Now we can switch desktops via [Ctrl]+[Alt]+[Left]/[Right] **and spin the cube via [Ctrl]+[Alt]+[Left Mousebutton] (or via middle-click on the desktop).**

---

### Post by kevdog on 2007-09-21
Well that did it!!! Not very laptop friendly since I dont have a mouse, but I managed to do it nonetheless with the touchpad -- very awkward.  I guess I could change the mappings in the rotate cube module correct??

---

### Post by Sammm_ on 2007-09-21
After reinstalling and then trying to run it without XGL as you suggested, I get this error...

```
sam@xubuntu:~$ compiz --replace
/usr/bin/compiz.real (core) - Error: Could not acquire compositing manager selection on screen 0 display ":0.0"
/usr/bin/compiz.real (core) - Fatal: No manageable screens found on display :0.0

```

---

### Post by Forlong on 2007-09-21
[QUOTE="Sammm_"]```
Error: Could not acquire compositing manager selection
```[/QUOTE]
Make sure you have disabled Xfce's *own* composite effects before running Compiz.

---

### Post by Sammm_ on 2007-09-21
Running it now generates an error...

A handler is already registered for the path starting with path[0] = "org"

CompizFusion works now, but without window decorations.

**Edit:** I forgot to say, when I tried to reinstall from your repo nothing would install, it kept saying certain packages didnt have installation candidates, so I tried treviños repo then ccsm wouldnt work so I'm now trying to install from Amaranth's repos.

---

### Post by Forlong on 2007-09-21
And you did follow the "First Steps"? Particularly the one with the *Window Decoration* plugin.

---

### Post by Forlong on 2007-09-21
> **Sammm_ said:**
> **Edit:** I forgot to say, when I tried to reinstall from your repo nothing would install, it kept saying certain packages didnt have installation candidates, so I tried treviños repo then ccsm wouldnt work so I'm now trying to install from Amaranth's repos.
Aww... never mix repos.
Make sure to remove all of the packages as well as Treviño's repository before following the guide again.

---

### Post by Sammm_ on 2007-09-21
I forgot to post, because I got so carried away playing with all the settings, it's all installed and works perfectly! :] Cheers.

---

### Post by kevdog on 2007-09-21
Sorry to be such a bother, but how do I get the water effects to work???  Seems like this has caused a lot of confusion for other people on google.

Thanks

---

### Post by Forlong on 2007-09-22
> **kevdog said:**
>  how do I get the water effects to work???
Enable the *Water Effect* plugin and configure it's shortcuts the way you want.

Rain should be set to Shift+F9 by default, so this should work right away.

And I for myself have Initiate set to Ctrl+< (just click right next to Initiate in the Actions tab -  wait till it says "New accelerator..." and type the combination you want).


edit: oh, I don't know if the < key is anywhere near Ctrl on your keyboard. On a german keyboard it's right of Shift.

---

### Post by kevdog on 2007-09-22
Maybe I better go back to the basics school,

Ive got the initiate set the Cntl+. (which is the > key).
Ive got the Toggle Rain and Toggle Wiper set to Shift+F9 and Shift+F8 (The default settings)

So what do I do next???  How do I make it work??  I hit Cntl+. and nothing happens.  Do I have to assign another action for it to work?? On the same question, Toggle rain??? I hit Shift+F9 and nothing happens.  Could you be more specific?? 

Thanks

---

### Post by Forlong on 2007-09-22
Your graphics card must support [pixel shader](http://en.wikipedia.org/wiki/Pixel_shader) version 1.3 or higher and your driver needs to support it.

If you get any output with that:
```
glxinfo | grep GL_ARB_fragment_program
```
you're good to go.

---

### Post by kevdog on 2007-09-22
Well I guess that answers my question b/c I dont get anything with that grep statement, so I guess no water effects for me!!!!

The emerald theme "popped on suddenly" but then when I restarted compiz from the command line -- no emerald theme.    Im using your stock ini file.  What do I have to do to restart emerald?

---

### Post by Forlong on 2007-09-22
> **kevdog said:**
>  What do I have to do to restart emerald?
```
emerald --replace
```
If it doesn't work, please post the output.

---

### Post by Bigdeath on 2007-09-22
Forlong your step by step worked I just couldn't get emerald working. I get the whick warning when I do emerald --replace.

---

### Post by Forlong on 2007-09-22
> **Bigdeath said:**
> I get the whick warning when I do emerald --replace.
The libwnck warning is normal on Feisty. It's finally fixed in Gutsy.

So Emerald doesn't work? Is there any output besides that?
If you use a Nvidia card, try what I wrote in the *Troubleshooting* section for *Nvidia user*

---

### Post by tomi_hl on 2007-09-22
I'm using ATI Radeon 9800XT

Since my driver is set to vesa, i followed your direction to change it to "radeon" and nothing else. However when i restart, all i got was a blank screen. 

Please help, I'm new to linux.

---

### Post by Decline- on 2007-09-22
Hi there Forlong.

Have you got any tips regarding tweaking compiz fusion for ATI/XGL? I think it seems a bit slow after some use... especially when it comes to the cube...

Any tweaking in xorg.conf? And what about indrect rendering, sync to vblank, and detect refresh rate - they don't seem to make a big difference, was it only in the old beryl days those options made a difference? :)

---

### Post by kevdog on 2007-09-22
When I type emerald --replace at the command line -- nothing happens.  I waited for like 5 minutes -- nothing happened.  I eventually hit cntl-c.  No output was sent to the command terminal either.

---

### Post by Bigdeath on 2007-09-22
I know this is a noobish question but to upgrade to gusty do I need to do a clean install or can I just upgrade?

---

### Post by kevdog on 2007-09-22
You can do just an upgrade if you want.  It will workl

---

### Post by Bigdeath on 2007-09-22
Cool thanks alot. One thing though I use Ubuntu studio. Will it change the lowlatency kernel?

---

### Post by kevdog on 2007-09-22
Im not sure if the gusty kernel contains a low-latency version in their standard distribution.  Might want to make another post in the Gusty section


Update
Started compiz --replace in command terminal, and then closed command terminal.  Then the emerald effects started???  Whats with that?

---

### Post by Forlong on 2007-09-23
> **tomi_hl said:**
> I'm using ATI Radeon 9800XT

Since my driver is set to vesa, i followed your direction to change it to "radeon" and nothing else. However when i restart, all i got was a blank screen. 

Please help, I'm new to linux.
Please post your xorg.conf here - and use the forum's CODE tag (# button)
> **Decline- said:**
> Have you got any tips regarding tweaking compiz fusion for ATI/XGL? I think it seems a bit slow after some use... especially when it comes to the cube...

Any tweaking in xorg.conf?
No, I'm beyond that. Tried a lot of crazy stuff back in the Beryl days and it never really had an effect. So right now I'm just using the xorg.conf that came with Ubuntu. Makes no difference to me.
> **Decline- said:**
> And what about indrect rendering, sync to vblank, and detect refresh rate - they don't seem to make a big difference, was it only in the old beryl days those options made a difference? :)
That's mostly taken care of by the compiz-wrapper (/usr/bin/compiz) now. And again, it never made any difference for me. It's either working or not. ^^
> **Bigdeath said:**
> Cool thanks alot. One thing though I use Ubuntu studio. Will it change the lowlatency kernel?
AFAIK the lowlatency kernel comes from the Ubuntu repositories anyway.
> **kevdog said:**
> Started compiz --replace in command terminal, and then closed command terminal.  Then the emerald effects started???  Whats with that?
Who cares if it works? ^^
I guess you just had to kill something with the --replace command and since emerald is set in the decoration plugin, *then* it took over.

---

### Post by tomi_hl on 2007-09-23
> **Forlong said:**
> Please post your xorg.conf here - and use the forum's CODE tag (# button)


```

# /etc/X11/xorg.conf (xorg X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the xorg.conf(5) manual page.
# (Type "man xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "Files"
	FontPath	"/usr/share/fonts/X11/misc"
	FontPath	"/usr/share/fonts/X11/cyrillic"
	FontPath	"/usr/share/fonts/X11/100dpi/:unscaled"
	FontPath	"/usr/share/fonts/X11/75dpi/:unscaled"
	FontPath	"/usr/share/fonts/X11/Type1"
	FontPath	"/usr/share/fonts/X11/100dpi"
	FontPath	"/usr/share/fonts/X11/75dpi"
	# path to defoma fonts
	FontPath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
	Load	"i2c"
	Load	"bitmap"
	Load	"ddc"
	Load	"dri"
	Load	"extmod"
	Load	"freetype"
	Load	"glx"
	Load	"int10"
	Load	"vbe"
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"us"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"		"/dev/input/mice"
	Option		"Protocol"		"ImPS/2"
	Option		"ZAxisMapping"		"4 5"
	Option		"Emulate3Buttons"	"true"
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"stylus"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"		"stylus"
	Option		"ForceDevice"	"ISDV4"		# Tablet PC ONLY
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"eraser"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"		"eraser"
	Option		"ForceDevice"	"ISDV4"		# Tablet PC ONLY
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"cursor"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"		"cursor"
	Option		"ForceDevice"	"ISDV4"		# Tablet PC ONLY
EndSection

Section "Device"
	Identifier	"Generic Video Card"
	Driver		"vesa"
	BusID		"PCI:1:0:0"
EndSection

Section "Monitor"
	Identifier	"E70f"
	Option		"DPMS"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Generic Video Card"
	Monitor		"E70f"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
	InputDevice     "stylus"	"SendCoreEvents"
	InputDevice     "cursor"	"SendCoreEvents"
	InputDevice     "eraser"	"SendCoreEvents"
EndSection

Section "DRI"
	Mode	0666
EndSection

```

---

### Post by Forlong on 2007-09-23
Try this:
```
sudo dpkg-reconfigure xserver-xorg
```
choose **ati** when asked for a driver.
And try to set the rest as good as possible (look for your monitor's manual first), but if you don't have a clue what to answer, it's mostly safe to press enter.

---

### Post by tomi_hl on 2007-09-23
> **Forlong said:**
> Try this:
```
sudo dpkg-reconfigure xserver-xorg
```
choose **ati** when asked for a driver.
And try to set the rest as good as possible (look for your monitor's manual first), but if you don't have a clue what to answer, it's mostly safe to press enter.

I got a blank screen again, here's the xorg.conf after i ran the above code and change the driver to ati.
```
# /etc/X11/xorg.conf (xorg X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the xorg.conf(5) manual page.
# (Type "man xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "Files"
	FontPath	"/usr/share/fonts/X11/misc"
	FontPath	"/usr/share/fonts/X11/cyrillic"
	FontPath	"/usr/share/fonts/X11/100dpi/:unscaled"
	FontPath	"/usr/share/fonts/X11/75dpi/:unscaled"
	FontPath	"/usr/share/fonts/X11/Type1"
	FontPath	"/usr/share/fonts/X11/100dpi"
	FontPath	"/usr/share/fonts/X11/75dpi"
	# path to defoma fonts
	FontPath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
	Load	"bitmap"
	Load	"ddc"
	Load	"dri"
	Load	"extmod"
	Load	"freetype"
	Load	"glx"
	Load	"int10"
	Load	"vbe"
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"us"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"		"/dev/input/mice"
	Option		"Protocol"		"ImPS/2"
	Option		"ZAxisMapping"		"4 5"
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"stylus"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"		"stylus"
	Option		"ForceDevice"	"ISDV4"		# Tablet PC ONLY
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"eraser"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"		"eraser"
	Option		"ForceDevice"	"ISDV4"		# Tablet PC ONLY
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"cursor"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"		"cursor"
	Option		"ForceDevice"	"ISDV4"		# Tablet PC ONLY
EndSection

Section "Device"
	Identifier	"ATI Radeon 9800XT"
	Driver		"ati"
	BusID		"PCI:1:0:0"
EndSection

Section "Monitor"
	Identifier	"ViewSonic E70f"
	Option		"DPMS"
	HorizSync	28-51
	VertRefresh	43-60
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"ATI Radeon 9800XT"
	Monitor		"ViewSonic E70f"
	DefaultDepth	16
	SubSection "Display"
		Depth		1
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
	InputDevice     "stylus"	"SendCoreEvents"
	InputDevice     "cursor"	"SendCoreEvents"
	InputDevice     "eraser"	"SendCoreEvents"
EndSection

Section "DRI"
	Mode	0666
EndSection
```

Is there any plugin or driver that i need to install first??

thank you

---

### Post by Forlong on 2007-09-23
Did you put Compiz in the autostart?

Please post the output of
```
cat ~/.gconf/desktop/gnome/applications/window_manager/%gconf.xml
```

---

### Post by Bigdeath on 2007-09-23
You could use envy. It will configure your xorg.conf and install the new nvidia driver that IMO has a few less bugs.

You can get it here, it may be worth a try.

[http://albertomilone.com/ubuntu/nvidia/scripts/envy_0.9.7-0ubuntu8_all.deb](http://albertomilone.com/ubuntu/nvidia/scripts/envy_0.9.7-0ubuntu8_all.deb)

When the screen pops up just hit OK.

---

### Post by tomi_hl on 2007-09-23
> **Forlong said:**
> Did you put Compiz in the autostart?

Please post the output of
```
cat ~/.gconf/desktop/gnome/applications/window_manager/%gconf.xml
```

no i didn't.

```
<?xml version="1.0"?>
<gconf>
        <entry name="current" mtime="1190569760" type="string">
                <stringvalue>/usr/bin/metacity</stringvalue>
        </entry>
        <entry name="default" mtime="1190476146" type="string">
                <stringvalue>/usr/bin/metacity</stringvalue>
        </entry>
</gconf>

```

here's the lspci output
```
00:00.0 Host bridge: Intel Corporation 82850 850 (Tehama) Chipset Host Bridge (MCH) (rev 02)
00:01.0 PCI bridge: Intel Corporation 82850 850 (Tehama) Chipset AGP Bridge (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 04)
00:1f.0 ISA bridge: Intel Corporation 82801BA ISA Bridge (LPC) (rev 04)
00:1f.1 IDE interface: Intel Corporation 82801BA IDE U100 (rev 04)
00:1f.2 USB Controller: Intel Corporation 82801BA/BAM USB (Hub #1) (rev 04)
00:1f.3 SMBus: Intel Corporation 82801BA/BAM SMBus (rev 04)
00:1f.4 USB Controller: Intel Corporation 82801BA/BAM USB (Hub #2) (rev 04)
01:00.0 VGA compatible controller: ATI Technologies Inc RV350 NJ [Radeon 9800 XT]
01:00.1 Display controller: ATI Technologies Inc RV350 NJ [Radeon 9800 XT] (Secondary)
02:09.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 50)
02:09.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 50)
02:09.2 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 51)
02:0a.0 Multimedia audio controller: Ensoniq 5880 AudioPCI (rev 02)
02:0b.0 Ethernet controller: Lite-On Communications Inc LNE100TX (rev 21)

```

Based on the lspci output i changed the Display device identifier to "ATI Technologies Inc RV350 NJ [Radeon 9800 XT]" with "ati" as the driver.

---

### Post by kingofpain on 2007-09-23
Does anybody know how to make menus semi-transparent?

---

### Post by Forlong on 2007-09-23
@tomi_hl: I'm truly sorry but this is really hardware-related.
I can't make out any trace that Compiz is the cause of your trouble and since I'm out of ideas, I recommend starting a separate thread about why the driver doesn't work for you.
I guess the Hardware forum would be the appropriate place for that.

> **kingofpain said:**
> Does anybody know how to make menus semi-transparent?
[How to set up Compiz Fusion](http://forlong.blogage.de/article/2007/8/29/How-to-set-up-Compiz-Fusion) &#8594; Transparency &#8594; Transparent panels and menus

---

### Post by SSB on 2007-09-23
Why is there an unupdatable compiz-core package in my update manager?

---

### Post by Forlong on 2007-09-23
From the guide:
> Due to a bug, the version number of compiz-core doesn't get updated and therefore Synaptic wants to upgrade the package all the time, although it's already the latest available. So it's best to remove the repository after we have installed every package we need: all we have to do is uncheck the box next to the repository at **Settings &#8594; Repositories &#8594; Third Party Software**

---

### Post by Papillonrus on 2007-09-23
I'm wondering if I can install compiz fusion along side of Beryl?  I should be able to change between sessions?  Is it Possible?  Thanks, Darrell

---

### Post by Bigdeath on 2007-09-23
Thats the way I got mine set up, I can even use the beryl icon to switch to compiz but emerald doesnt work with compiz for me.

---

### Post by kingofpain on 2007-09-23
> **Forlong said:**
> 
[How to set up Compiz Fusion](http://forlong.blogage.de/article/2007/8/29/How-to-set-up-Compiz-Fusion) &#8594; Transparency &#8594; Transparent panels and menus
Thanks. Great site you've got there.=D>

---

### Post by Papillonrus on 2007-09-23
Let me ask which "How To" did you use?  I tried a couple and they just froze up.  I couldn't do anything.  On one I could have rebuilt in terminal, but I'm too new for that.  spend 45 min. to an hour for install.  guide me to the correct "How To"  Thanks, Darrell

---

### Post by Bigdeath on 2007-09-23
forlongs works well Like i said I always get this when i try to start compiz --replace
j> oe@ubuntu:~$ compiz --replace
/usr/bin/compiz.real (decoration) - Warn: Property ignored because version is 20061011 and decoration plugin version is 20070319

/usr/bin/compiz.real (decoration) - Warn: Property ignored because version is 20061011 and decoration plugin version is 20070319

/usr/bin/compiz.real (decoration) - Warn: Property ignored because version is 20061011 and decoration plugin version is 20070319

/usr/bin/compiz.real (core) - Error: no 'text' plugin with ABI version '20070902' loaded

/usr/bin/compiz.real (ring) - Warn: No compatible text plugin found.
/usr/bin/compiz.real (core) - Error: no 'text' plugin with ABI version '20070902' loaded

/usr/bin/compiz.real (thumbnail) - Warn: No compatible text plugin found.
/usr/bin/compiz.real (cube) - Warn: Failed to load slide: /usr/share/compiz/default-cubecap.png
/usr/bin/compiz.real (cubecaps) - Warn: Failed to load image: fusioncap.png
/usr/bin/compiz.real (cubecaps) - Warn: Failed to load image: compizcap.png
/usr/bin/compiz.real (splash) - Warn: Could not load splash background image "splash_background.png" !
/usr/bin/compiz.real (splash) - Warn: Could not load splash logo image "splash_logo.png" !






And this with emerald --replace

> oe@ubuntu:~$ emerald --replace

(emerald:9653): Wnck-WARNING **: Unhandled action type (nil)

(emerald:9653): Wnck-WARNING **: Unhandled action type (nil)

(emerald:9653): Wnck-WARNING **: Unhandled action type (nil)

(emerald:9653): Wnck-WARNING **: Unhandled action type (nil)

(emerald:9653): Wnck-WARNING **: Unhandled action type (nil)

(emerald:9653): Wnck-WARNING **: Unhandled action type (nil)

(emerald:9653): Wnck-WARNING **: Unhandled action type (nil)

(emerald:9653): Wnck-WARNING **: Unhandled action type (nil)

(emerald:9653): Wnck-WARNING **: Unhandled action type (nil)

(emerald:9653): Wnck-WARNING **: Unhandled action type (nil)

(emerald:9653): Wnck-WARNING **: Unhandled action type (nil)

(emerald:9653): Wnck-WARNING **: Unhandled action type (nil)

(emerald:9653): Wnck-WARNING **: Unhandled action type (nil)

(emerald:9653): Wnck-WARNING **: Unhandled action type (nil)

(emerald:9653): Wnck-WARNING **: Unhandled action type (nil)

(emerald:9653): Wnck-WARNING **: Unhandled action type (nil)

(emerald:9653): Wnck-WARNING **: Unhandled action type (nil)

(emerald:9653): Wnck-WARNING **: Unhandled action type (nil)

(emerald:9653): Wnck-WARNING **: Unhandled action type (nil)

(emerald:9653): Wnck-WARNING **: Unhandled action type (nil)

(emerald:9653): Wnck-WARNING **: Unhandled action type (nil)

(emerald:9653): Wnck-WARNING **: Unhandled action type (nil)

(emerald:9653): Wnck-WARNING **: Unhandled action type (nil)

(emerald:9653): Wnck-WARNING **: Unhandled action type (nil)

(emerald:9653): Wnck-WARNING **: Unhandled action type (nil)

(emerald:9653): Wnck-WARNING **: Unhandled action type (nil)

(emerald:9653): Wnck-WARNING **: Unhandled action type (nil)

(emerald:9653): Wnck-WARNING **: Unhandled action type (nil)

(emerald:9653): Wnck-WARNING **: Unhandled action type (nil)

(emerald:9653): Wnck-WARNING **: Unhandled action type (nil)

(emerald:9653): Wnck-WARNING **: Unhandled action type (nil)

(emerald:9653): Wnck-WARNING **: Unhandled action type (nil)



---

### Post by Forlong on 2007-09-24
> **Papillonrus said:**
> I'm wondering if I can install compiz fusion along side of Beryl?  I should be able to change between sessions?  Is it Possible?
Yes it is possible but it will leave you without window boarders (everything else will work, though), because neither Emerald nor GWD (gtk-window-decorator) are compatible with both.
*Theoretically* you could try installing Compiz Fusion without updating Emerald.
This way you will have GWD for Compiz and Emerald for Beryl. Haven't tested this, though.
> **Papillonrus said:**
> Let me ask which "How To" did you use?  I tried a couple and they just froze up.  I couldn't do anything.  On one I could have rebuilt in terminal, but I'm too new for that.  spend 45 min. to an hour for install.  guide me to the correct "How To"  Thanks, Darrell
This is a very unusual question in a thread, that is about a How-To. ;)
Of course, I'm going to tell you, that this one is *the* one to go. But I took the time to explain this in the introduction, so feel free to read it and decide afterwards, if that's what you want.
> **Bigdeath said:**
> ```
/usr/bin/compiz.real (decoration) - Warn: Property ignored because version is 20061011 and decoration plugin version is 20070319

/usr/bin/compiz.real (decoration) - Warn: Property ignored because version is 20061011 and decoration plugin version is 20070319

/usr/bin/compiz.real (decoration) - Warn: Property ignored because version is 20061011 and decoration plugin version is 20070319

/usr/bin/compiz.real (core) - Error: no 'text' plugin with ABI version '20070902' loaded

/usr/bin/compiz.real (ring) - Warn: No compatible text plugin found.
/usr/bin/compiz.real (core) - Error: no 'text' plugin with ABI version '20070902' loaded
```
You have messed up dependencies, which means you didn't remove Compiz prior to install or have still another third-party repository enabled.

---

### Post by Bigdeath on 2007-09-24
Even if the default decoration plugin is a different version, shouldn't emerald still work?

---

### Post by kingofpain on 2007-09-24
Oups, another problem. I followed your instructions and set emerald as window decoration. Everything just fine. But when I reboot, no window decoration. In compiz settings window decoration plugin appears unchecked again! :confused:
Doesn't matter if I check it, at reboot it is unchecked, so, no window decorations. :(

---

### Post by Forlong on 2007-09-24
> **Bigdeath said:**
> Even if the default decoration plugin is a different version, shouldn't emerald still work?
Emerald can't work on it's own.
And you need to fix this anyway.
> **kingofpain said:**
> when I reboot, no window decoration. In compiz settings window decoration plugin appears unchecked again! :confused:
Did you switch to the Flat-file Backend?

---

### Post by benhur99ph on 2007-09-24
Hey! Great guide! Thanks a lot! I managed to install compiz-fusion without any problems.

---

### Post by kingofpain on 2007-09-24
> **Forlong said:**
> Did you switch to the Flat-file Backend?

Yes, I did. It was like this by default. I just made a new profile.

---

### Post by Forlong on 2007-09-24
> **kingofpain said:**
> Yes, I did. It was like this by default. I just made a new profile.
Please post the output of
```
dpkg -l |grep compiz
```

---

### Post by kingofpain on 2007-09-24
> **Forlong said:**
> Please post the output of
```
dpkg -l |grep compiz
``````

[FONT="Courier New"]
ii  compiz-core                                0.5.2+git20070829-0ubuntu1amaranth1    OpenGL window and compositing manager
ii  compiz-fusion-plugins-extra                0.5.2+git20070829-0ubuntu1~ppa1        Collection of extra plugins from OpenComposi
ii  compiz-fusion-plugins-main                 0.5.2+git20070829-0ubuntu1~ppa1        Collection of plugins from OpenCompositing f
rc  compiz-gnome                               0.5.2+git20070829-0ubuntu1amaranth1    OpenGL window and compositing manager - GNOM
rc  compiz-gtk                                 0.3.6-1ubuntu13                        OpenGL window and compositing manager - Gtk 
ii  compiz-plugins                             0.5.2+git20070829-0ubuntu1amaranth1    OpenGL window and compositing manager - plug
ii  compizconfig-settings-manager              0.5.2+git20070829-0ubuntu1~ppa1        Compiz configuration settings manager
ii  emerald                                    0.3~git20070717-0ubuntu1~ppa1          Decorator for compiz-fusion
rc  gnome-compiz-manager                       0.10.3-0ubuntu1                        Compiz Gnome Manager
ii  libcompizconfig-backend-gconf              0.5.2+git20070829-0ubuntu1~ppa1        Settings library for plugins - OpenCompositi
ii  libcompizconfig0                           0.5.2+git20070829-0ubuntu1~ppa1        Settings library for plugins - OpenCompositi
ii  libemeraldengine0                          0.3~git20070717-0ubuntu1~ppa1          Decoration engines for compiz-fusion
ii  python-compizconfig                        0.5.2+git20070829-0ubuntu1~ppa1        Compiz configuration system bindings[/FONT]

```

---

### Post by PuppyFromHell on 2007-09-24
Ok, everything installed okay, but when compiz is running with two or more windows open it crashes to the login screen.  I think it also does this when I try to close a window.  It kind of fades out, my blueish background gets some orange highlights.  Does anyone know what is going on?

---

### Post by ST.x on 2007-09-24
whats the difference between Amaranth's and Trevino's repos?

---

### Post by Forlong on 2007-09-25
@kingofpain:

Try deleting configs of removed packages:
```
sudo dpkg --purge compiz-gtk compiz-gnome gnome-compiz-manager
```

If it still doesn't work, you can delete the cofings in your home-folder as well:
```
rm -r ~/.config/compiz
```
And you can delete the gconf-keys too:
```
rm -r ~/.gconf/apps/compiz
```
You should reboot then. The folder will get created again, when you run Compiz for the first time.

---

### Post by Forlong on 2007-09-25
Sorry, I got interrupted earlier.
> **PuppyFromHell said:**
> Ok, everything installed okay, but when compiz is running with two or more windows open it crashes to the login screen.  I think it also does this when I try to close a window.  It kind of fades out, my blueish background gets some orange highlights.  Does anyone know what is going on?
Sounds like a hardware problem to me. You should consider starting a separate thread in the Hardware section,
Give as much infos as you can about your system, especially the graphics card and it's driver.
> **ST.x said:**
> whats the difference between Amaranth's and Trevino's repos?
I pretty much answered this in the introduction of the main guide. Treviño's is one of the "bleeding edge repositories" I referred to.

---

### Post by kingofpain on 2007-09-25
**@Forlong**
Ok, I've figured it out. It's got something to do with plugins. It seems that, when I enable/disable a plugin, something gets screwed up. I've tested: animations, desktop wall and wobbly windows.

If I create a new profile with everything set by default, it works fine.:confused:

My transparency settings don't generate this problem, though. So, I guess it must be something related to plugins.

---

### Post by PuppyFromHell on 2007-09-25
Well Trevino's repos worked for a while and then it crashed so I thought I'd try amaranth's.  Anyway:
Dell Inspiron 9300
Pentium M 1.6 GHz
ATI Mobility M300 (I don't know the driver)
512 MB RAM

---

### Post by Dvorakis on 2007-09-25
I currently used this method to install...and Im recieving some problems.

My compiz settings manager isn't working anymore.

When I've reinstalled the problem persists.

I also had a problem with no window boarders,and I was wondering why.

---

### Post by Forlong on 2007-09-25
> **Dvorakis said:**
> My compiz settings manager isn't working anymore.
Post the output of
```
dpkg -l | grep compiz
```

---

### Post by Dvorakis on 2007-09-25
ii  compiz                                     0.5.2+git20070918-0ubuntu5~ppa1            OpenGL window and compositing manager
ii  compiz-core                                0.5.2+git20070918-0ubuntu5~ppa1            OpenGL window and compositing manager
ii  compiz-fusion-plugins-extra                0.5.2+git20070917-0ubuntu1~ppa1            Collection of extra plugins from OpenComposi
ii  compiz-fusion-plugins-main                 0.5.2+git20070917-0ubuntu3~ppa1            Collection of plugins from OpenCompositing f
ii  compiz-gnome                               0.5.2+git20070918-0ubuntu5~ppa1            OpenGL window and compositing manager - GNOM
rc  compiz-gtk                                 0.3.6-1ubuntu13                            OpenGL window and compositing manager - Gtk 
ii  compiz-plugins                             0.5.2+git20070918-0ubuntu5~ppa1            OpenGL window and compositing manager - plug
ii  compizconfig-settings-manager              0.5.2+git20070829-0ubuntu1~ppa1            Compiz configuration settings manager
ii  emerald                                    0.3~git20070717-0ubuntu1~ppa1              Decorator for compiz-fusion
ii  libcompizconfig-backend-gconf              0.5.2+git20070918-0ubuntu1~ppa1            Settings library for plugins - OpenCompositi
ii  libcompizconfig0                           0.5.2+git20070919-0ubuntu2~ppa1            Settings library for plugins - OpenCompositi
ii  libemeraldengine0                          0.3~git20070717-0ubuntu1~ppa1              Decoration engines for compiz-fusion
ii  python-compizconfig                        0.5.2+git20070829-0ubuntu1~ppa1            Compiz configuration system bindings

---

### Post by Forlong on 2007-09-25
Please post your sources.list - and use the CODE tag this time (# button):
```
grep -v ^## /etc/apt/sources.list
```

---

### Post by Dvorakis on 2007-09-25
```
deb http://us.archive.ubuntu.com/ubuntu/ feisty main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ feisty main restricted

deb http://us.archive.ubuntu.com/ubuntu/ feisty-updates main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ feisty-updates main restricted

# deb http://us.archive.ubuntu.com/ubuntu/ edgy universe
# deb-src http://us.archive.ubuntu.com/ubuntu/ edgy universe

# deb http://us.archive.ubuntu.com/ubuntu/ edgy-backports main restricted universe multiverse
# deb-src http://us.archive.ubuntu.com/ubuntu/ edgy-backports main restricted universe multiverse

deb http://security.ubuntu.com/ubuntu feisty-security main restricted
deb-src http://security.ubuntu.com/ubuntu feisty-security main restricted
# deb http://security.ubuntu.com/ubuntu edgy-security universe
# deb-src http://security.ubuntu.com/ubuntu edgy-security universe
deb http://ppa.launchpad.net/amaranth/ubuntu feisty main
# deb http://archive.ubuntustudio.org/ubuntustudio feisty main
dvorak@dvorak-desktop:~$ grep -v ^## /etc/apt/sources.list

deb http://us.archive.ubuntu.com/ubuntu/ feisty main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ feisty main restricted

deb http://us.archive.ubuntu.com/ubuntu/ feisty-updates main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ feisty-updates main restricted

# deb http://us.archive.ubuntu.com/ubuntu/ edgy universe
# deb-src http://us.archive.ubuntu.com/ubuntu/ edgy universe

# deb http://us.archive.ubuntu.com/ubuntu/ edgy-backports main restricted universe multiverse
# deb-src http://us.archive.ubuntu.com/ubuntu/ edgy-backports main restricted universe multiverse

deb http://security.ubuntu.com/ubuntu feisty-security main restricted
deb-src http://security.ubuntu.com/ubuntu feisty-security main restricted
# deb http://security.ubuntu.com/ubuntu edgy-security universe
# deb-src http://security.ubuntu.com/ubuntu edgy-security universe
deb http://ppa.launchpad.net/amaranth/ubuntu feisty main
# deb http://archive.ubuntustudio.org/ubuntustudio feisty main

```

Sorry,I don't think anything was wrong...It just didn't work the last couple times I tried to install it.
I could try again if you can't figure it out.

---

### Post by Forlong on 2007-09-25
Please do this:
```
sudo apt-get update && sudo apt-get upgrade
```
Your packages are not the latest ones of the repository.

---

### Post by Dvorakis on 2007-09-25
Ok,I did that.And it still didn't work...so I tried over from the beggining,and still no luck.

---

### Post by Forlong on 2007-09-25
edit: do this first:
```
sudo dpkg --purge compiz-gtk
```


This is how th output of ```
dpkg -l | grep compiz
``` should look like:
```
ii  compiz                                     0.5.2+git20070829-0ubuntu1amaranth1    OpenGL window and compositing manager
ii  compiz-core                                0.5.2+git20070829-0ubuntu1amaranth1    OpenGL window and compositing manager
ii  compiz-fusion-plugins-extra                0.5.2+git20070829-0ubuntu1~ppa1        Collection of extra plugins from OpenComposi
ii  compiz-fusion-plugins-main                 0.5.2+git20070829-0ubuntu1~ppa1        Collection of plugins from OpenCompositing f
ii  compiz-gnome                               0.5.2+git20070829-0ubuntu1amaranth1    OpenGL window and compositing manager - GNOM
ii  compiz-plugins                             0.5.2+git20070829-0ubuntu1amaranth1    OpenGL window and compositing manager - plug
ii  compizconfig-settings-manager              0.5.2+git20070829-0ubuntu1~ppa1        Compiz configuration settings manager
ii  emerald                                    0.3~git20070717-0ubuntu1~ppa1          Decorator for compiz-fusion
ii  libcompizconfig-backend-gconf              0.5.2+git20070829-0ubuntu1~ppa1        Settings library for plugins - OpenCompositi
ii  libcompizconfig0                           0.5.2+git20070829-0ubuntu1~ppa1        Settings library for plugins - OpenCompositi
ii  libemeraldengine0                          0.3~git20070717-0ubuntu1~ppa1          Decoration engines for compiz-fusion
ii  python-compizconfig                        0.5.2+git20070829-0ubuntu1~ppa1        Compiz configuration system bindings
```
Is that the case now?

---

### Post by Dvorakis on 2007-09-25
Yeah...Thats what they look like...Unless I missed something.But the compiz fusion config still doesn't work...and I can't figure out why.

---

### Post by Forlong on 2007-09-25
What's the output of ```
ccsm
``` in the terminal?

---

### Post by Bart_D on 2007-09-25
In general, I found that after following the Blog, I needed to modify my xorg.conf to change Composite to Enable.....I don;t know if Forlong has added a command for this or what but I had to change xorg.conf AFTER backing it up.  So I changed it, restarted and had to setup Cf to autostart to start on boot.  To run it manually, I followed his command.  

Note: Before restarting for the first time(right after changing my xorg.conf, I also changed my videocard setting to allow Window Borders...again this was done in xorg.conf and this too was done AFTER backing up xorg.  It did not work for me in Xubuntu but I just press Alt+drag to move windows so I really couldn;t care less...plus I won;t be changing themes so I don;t mind, as long as the other features work.

---

### Post by Dvorakis on 2007-09-25
```
Info: No sexy-python package found, don't worry it's optional.
Traceback (most recent call last):
  File "/usr/local/bin/ccsm", line 45, in <module>
    idle = ccm.IdleSettingsParser(context)
  File "/usr/local/lib/python2.5/site-packages/ccm/Utils.py", line 229, in __init__
    self.Context.Plugins.items ())
  File "/usr/local/lib/python2.5/site-packages/ccm/Utils.py", line 228, in <lambda>
    self.PluginList = filter (lambda p: FilterPlugin (p[1]),
  File "/usr/local/lib/python2.5/site-packages/ccm/Utils.py", line 225, in FilterPlugin
    return not p.Initialized and p.Enabled
AttributeError: 'compizconfig.Plugin' object has no attribute 'Initialized'


```

---

### Post by Forlong on 2007-09-26
Dvorakis, did you compile Compiz yourself or used some script to install it before?

---

### Post by Forlong on 2007-09-27
Hi everybody,

the repository from the main guide has been updated to Gutsy-status.

Users of the old repository (from the KDE/Xfce guide) can now switch to the new one.

And if you're using Emerald it's much easier, because now Emerald is checked before gtk-window-decorator, so you don't have to use any startscript or the like anymore.

But that means it's for the users of GWD the other way round now: they have to use a startscript or remove Emerald (of course only if it was installed before, if not, you won't notice any difference).

Other changes include a little different default animations and the updated blacklist in the compiz-wrapper.


Regards,
Nick


P.S. the compiz-core update-issue has not been fixed.

---

### Post by ST.x on 2007-09-27
^ So to upgrade to the new version, would I just enable that repo and upgrade all the available ones from there?

---

### Post by vortex_noob on 2007-09-27
is the new update dated september 19 from amaranth repos safe to use? I'm afraid to break CF like it did when i was using trevino's repos last month. This one is using a fresh install ubuntu with amaranth's and working quite satisfactory since then. I won't mess with any update that is not quite certain to work. Any thoughts?

---

### Post by Forlong on 2007-09-27
> **ST.x said:**
> ^ So to upgrade to the new version, would I just enable that repo and upgrade all the available ones from there?
Yes, if you followed the main guide.
If you used the How-To for KDE/Xfce, you'd have to switch to the repository mentioned in the main guide.
> **vortex_noob said:**
> is the new update dated september 19 from amaranth repos safe to use? I'm afraid to break CF like it did when i was using trevino's repos last month.
Compiz Fusion will most definitely not break.
There's a tiny possibility that your card could be blacklisted now but then we'll find a solution for that.

---

### Post by peas on my plate on 2007-09-27
Thank you Forlong for your blog!  I installed compiz-fusion today without via the terminal without any problems.  But...none of the effects work.  As best as I can describe it, when I run compiz --replace, the screen flickers, but nothing changes.  Here is the terminal output:
> Checking for Xgl: not present. 
Checking for texture_from_pixmap: not present. 
Trying again with indirect rendering:
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
Checking for nVidia: not present. 
Checking for Xgl: not present. 

(gtk-window-decorator:10444): Wnck-WARNING **: Unhandled action type (nil)

(gtk-window-decorator:10444): Wnck-WARNING **: Unhandled action type (nil)

(gtk-window-decorator:10444): Wnck-WARNING **: Unhandled action type (nil)

(gtk-window-decorator:10444): Wnck-WARNING **: Unhandled action type (nil)

(gtk-window-decorator:10444): Wnck-WARNING **: Unhandled action type (nil)

(gtk-window-decorator:10444): Wnck-WARNING **: Unhandled action type (nil)

(gtk-window-decorator:10444): Wnck-WARNING **: Unhandled action type (nil)

(gtk-window-decorator:10444): Wnck-WARNING **: Unhandled action type (nil)

(gtk-window-decorator:10444): Wnck-WARNING **: Unhandled action type (nil)

(gtk-window-decorator:10444): Wnck-WARNING **: Unhandled action type (nil)
/usr/bin/compiz.real: symbol lookup error: /usr/lib/compiz/libdecoration.so: undefined symbol: decor_apply_gravity


Here is my graphics card information, in case you need it:
Identifer       "ATI Technologies Inc Radeon R250 [Mobility FireGL 9000]"
Driver		"ati"
BusID		"PCI:1:0:0"

Sorry to add yet another post to an already long thread (I've already read most of it!) but I can't think of anything else to do.  I know the answer's got to be obvious but I can't see it! :confused: any help would be appreciated-

---

### Post by scottsark on 2007-09-27
Great guide! Everything went well with my install today, The effects are nice. I have one problem though, when I try to install emerald from the Synaptic Package Manager as mentioned in the guide I get:

emerald:
 Depends: libemeraldengine0 but it is not going to be installed


I get the reverse when I try to install libemeraldengine0.

I can't install emerald at all but everything else went extremely smooth. Any help would be appreciated. Sorry if it's a noob question as I am a noob.

---

### Post by peas on my plate on 2007-09-28
I found the answer on the hitherto unexplored post #228.  Unbelievable, and embarrasingly obvious.  Thanks anyway!:oops:

---

### Post by Forlong on 2007-09-28
> **scottsark said:**
> when I try to install emerald from the Synaptic Package Manager as mentioned in the guide I get:

emerald:
 Depends: libemeraldengine0 but it is not going to be installed


I get the reverse when I try to install libemeraldengine0.

I can't install emerald at all but everything else went extremely smooth.
Did you try to install Emerald while installing everything else or afterwards?
In other words: is the repository still enabled?

If so, please run this in a terminal:
```
sudo apt-get install emerald
```
and post the output here.


> **peas on my plate said:**
> I found the answer on the hitherto unexplored post #228.  Unbelievable, and embarrasingly obvious.  Thanks anyway!:oops:
It's always great to see people solving their own problems. :)

---

### Post by scottsark on 2007-09-28
[QUOTE=Forlong;3440457]Did you try to install Emerald while installing everything else or afterwards?
In other words: is the repository still enabled?

Yes I did try to install it with everything else and afterwards as well.

If so, please run this in a terminal:
```
sudo apt-get install emerald
```
and post the output here.

scotty@scotty-desktop:~$ sudo apt-get install emerald
Password:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  emerald: Depends: libemeraldengine0 but it is not going to be installed
E: Broken packages



Thanks for the quick reply Forlong!

---

### Post by Forlong on 2007-09-28
Please run
```
sudo apt-get -f install
```
and try again.

---

### Post by limbourg31 on 2007-09-28
Whe I installed Compiz Fusion i couldn't even get the cube effect. Wobbly windows worked, though. I have only one window where it says "switch between workspaces" yet I set it in the compiz manager to 4. What am I doing wrong?

---

### Post by Forlong on 2007-09-29
Did you follow the *Getting the cube* section [here](http://forlong.blogage.de/article/2007/8/29/How-to-set-up-Compiz-Fusion) - particularly the "Secondly..." part?

---

### Post by drchaos619 on 2007-09-29
I'm running Ubuntu fiesty with an ATI 9800 pro card with compiz, emerald and avant.

My compiz has been working wonderfully since I got it all configured and sorted out. However, my video playback was choppy every time I put it into full screen. I already did the X11 video output method, but no dice.

I read about the graphics card driver prog called envy and decided to use it to see if it would solve my problems and voila, it did! however, compiz is shot, emerald is shot and avant is shot. I expected as much but I thought I could figure it out and get it back.

When I type either emerald --replace or compiz --replace in the terminal, I get the following replies:

emerald --replace

(emerald:6920): GLib-GObject-CRITICAL **: g_object_ref: assertion `G_IS_OBJECT (object)' failed

and for compiz:

compiz --replace
Fatal: Failed test: texture_from_pixmap support
Checks indicate that it's impossible to start compiz on your system.


I know this all started when I upgraded my graphics drivers

---

### Post by scottsark on 2007-09-29
Thanks again for the quick reply forlong. I followed your step and tried again to no avail. here is my results:

scotty@scotty-desktop:~$ sudo apt-get -f install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libberylsettings0 beryl-plugins-data libberyldecoration0
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 3 not upgraded.
scotty@scotty-desktop:~$ sudo apt-get install emerald
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  emerald: Depends: libemeraldengine0 but it is not going to be installed
E: Broken packages
scotty@scotty-desktop:~$ 

Sorry I'm such a noob, I feel like I should be able to figure this out myself but I ate a lot of paint chips as a kid.

---

### Post by Forlong on 2007-09-29
> **scottsark said:**
> 0 upgraded, 0 newly installed, 0 to remove and 3 not upgraded.
Please run
```
sudo apt-get update && sudo apt-get upgrade
```
and try again.

---

### Post by scottsark on 2007-09-29
Forlong, here are my results:

scotty@scotty-desktop:~$ sudo apt-get update && sudo apt-get upgrade
Password:
Ign [http://repoubuntusoftware.info](http://repoubuntusoftware.info) feisty Release.gpg
Ign [http://repoubuntusoftware.info](http://repoubuntusoftware.info) feisty/all Translation-en_US                
Ign [http://repoubuntusoftware.info](http://repoubuntusoftware.info) feisty Release                              
Ign [http://repoubuntusoftware.info](http://repoubuntusoftware.info) feisty/all Packages                         
Hit [http://repoubuntusoftware.info](http://repoubuntusoftware.info) feisty/all Packages                         
Get:1 [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty Release.gpg [191B]                      
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty/main Translation-en_US                    
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty/restricted Translation-en_US              

Get:2 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-updates Release.gpg [191B] 
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-updates/main Translation-en_US         
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-updates/restricted Translation-en_US   
Get:3 [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security Release.gpg [191B]            
Ign [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/main Translation-en_US          
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) feisty Release.gpg                                
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) feisty/main Translation-en_US           
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-updates Release              
Ign [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/restricted Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/universe Translation-en_US
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security Release                         
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) feisty Release                                    
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-updates/main Packages        
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/main Packages         
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) feisty/main Packages                    
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-updates/restricted Packages  
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) feisty/main Packages                    
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/restricted Packages   
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/main Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/restricted Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/universe Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/universe Sources
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty/universe Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty/multiverse Translation-en_US
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty Release
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty/restricted Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty/universe Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty/multiverse Packages
Fetched 3B in 2s (1B/s)
Reading package lists... Done
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be upgraded:
  compiz-core
1 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B/188kB of archives.
After unpacking 0B of additional disk space will be used.
Do you want to continue [Y/n]? y
WARNING: The following packages cannot be authenticated!
  compiz-core
Install these packages without verification [y/N]? y
(Reading database ... 113426 files and directories currently installed.)
Preparing to replace compiz-core 1:0.5.2+git20070918-0ubuntu5~ppa1 (using .../compiz-core_1%3a0.5.2+git20070918-0ubuntu5~ppa1_i386.deb) ...
Unpacking replacement compiz-core ...
Setting up compiz-core (0.5.2+git20070918-0ubuntu5~ppa1) ...


scotty@scotty-desktop:~$ sudo apt-get -f install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libberylsettings0 beryl-plugins-data libberyldecoration0
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 1 not upgraded.


scotty@scotty-desktop:~$ sudo apt-get install emerald
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  emerald: Depends: libemeraldengine0 but it is not going to be installed
E: Broken packages



Only one not upgraded now but still unable to get emerald or libemeraldengine0. Thanks again for your efforts so far.

---

### Post by Forlong on 2007-09-29
I am honestly out of ideas. It *should* work, apparently but why it doesn't... I don't know.

I can upload you the two packages tomorrow and you can try to install them manually.

---

### Post by diamondnular on 2007-09-30
Hi Forlong, I followed your guide and got everything installed fine. But after compiz --replace, I have black screen, just the title bar is visible. Any idea why is that?

Btw, I have Nvidia GeForce Go 6400 and have the lastest Nvidia driver installed.

Thanks,

KC.

PS: should have added here also: when Ctrl - Alt - Back Space, I got freezing windows and screens, mouse moves but nothing else works. I need to hard restart. Weird :(!

---

### Post by kris2pe on 2007-09-30
Not all the effects are working properly
Water doesn't work
Cover Switcher doesn't work
Problems w/ Workspace switcher!

---

### Post by Forlong on 2007-09-30
@scottsark: I attached the packages. Make sure to install **libemeraldengine0** first.

> **diamondnular said:**
> Hi Forlong, I followed your guide and got everything installed fine. But after compiz --replace, I have black screen, just the title bar is visible. Any idea why is that?

Btw, I have Nvidia GeForce Go 6400 and have the lastest Nvidia driver installed.

Thanks,

KC.

PS: should have added here also: when Ctrl - Alt - Back Space, I got freezing windows and screens, mouse moves but nothing else works. I need to hard restart. Weird :(!
Have a look at the guide at *Troubleshooting &#8594; Compiz doesn't work at all &#8594; Nvidia user* as well as *Compiz freezes randomly and/or permanently on logout*

> **kris2pe said:**
> Not all the effects are working properly
Water doesn't work
Cover Switcher doesn't work
Problems w/ Workspace switcher!
Water effects only works if your graphics card supports pixel shaders.

The other two should work though.
Post your output of
```
compiz --replace
```
in the terminal.

---

### Post by Faud on 2007-09-30
I followed the guide that you have linked Forlong and Compiz Fusion installed perfectly w/o any glitches. However it was using up a massive amount of my cpu...like up to 16-20 % Is this normal ?

I have a 2.8 processor, 2gig ram, 6200se nvidia. All of the effects worked great.

---

### Post by scottsark on 2007-09-30
Forlong, I'm off to Manhattan for 8 days of vacation in a few hours. I'll try to manually install when I get back and post my results. I just want to say thanks again for all your help. You have gone over and above my expectations for help a forum. If this is indicative of the ubuntu community then I'm even happier to ditch XP and jump into linux. I'll be back in a little over a week with a two day hangover.

---

### Post by diamondnular on 2007-09-30
> **Forlong said:**
> 
Have a look at the guide at *Troubleshooting &#8594; Compiz doesn't work at all &#8594; Nvidia user* as well as *Compiz freezes randomly and/or permanently on logout*


Yes, I checked that. No helps at all. :(

Now I manage to have it "somewhat" worked by Alt - F2 and type "compiz --replace --indirect-rendering. I said "somewhat" because it still has another problems. Now I do not have "black screen with top bar", but instead, I usually have "white" or "freeze" windows. Anybody experiences the same issue?

Thanks,

KC.

---

### Post by Forlong on 2007-09-30
To Faud and diamondnular: sorry I'm not experienced enough with Nvidia. :(
All of the things I know are pretty much in the guide, already...

---

### Post by m.ookie on 2007-09-30
Wow!  I am completely new to Ubuntu and this is the most perfect guide I've seen so far.

---

### Post by kris2pe on 2007-09-30
I am using an Nvidia 8600GT!!! 
Checking for Xgl: not present. 
Detected PCI ID for VGA: 02:00.0 0300: 10de:0402 (rev a1) (prog-if 00 [VGA])
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
Comparing resolution (1280x1024) to maximum 3D texture size (8192): Passed.
Checking for nVidia: present. 
Checking for FBConfig: present. 
Checking for Xgl: not present. 
Starting emerald

(emerald:7533): Wnck-WARNING **: Unhandled action type (nil)

(emerald:7533): Wnck-WARNING **: Unhandled action type (nil)

(emerald:7533): Wnck-WARNING **: Unhandled action type (nil)

(emerald:7533): Wnck-WARNING **: Unhandled action type (nil)

(emerald:7533): Wnck-WARNING **: Unhandled action type (nil)

(emerald:7533): Wnck-WARNING **: Unhandled action type (nil)

(emerald:7533): Wnck-WARNING **: Unhandled action type (nil)

(emerald:7533): Wnck-WARNING **: Unhandled action type (nil)

(emerald:7533): Wnck-WARNING **: Unhandled action type (nil)

(emerald:7533): Wnck-WARNING **: Unhandled action type (nil)

(emerald:7533): Wnck-WARNING **: Unhandled action type (nil)

(emerald:7533): Wnck-WARNING **: Unhandled action type (nil)

(emerald:7533): Wnck-WARNING **: Unhandled action type (nil)

(emerald:7533): Wnck-WARNING **: Unhandled action type (nil)

(emerald:7533): Wnck-WARNING **: Unhandled action type (nil)

(emerald:7533): Wnck-WARNING **: Unhandled action type (nil)

(emerald:7533): Wnck-WARNING **: Unhandled action type (nil)

(emerald:7533): Wnck-WARNING **: Unhandled action type (nil)

(emerald:7533): Wnck-WARNING **: Unhandled action type (nil)

(emerald:7533): Wnck-WARNING **: Unhandled action type (nil)
/usr/bin/compiz.real (video) - Warn: No 8 bit GLX pixmap format, disabling YV12 image format

(emerald:7533): Wnck-WARNING **: Unhandled action type (nil)

(emerald:7533): Wnck-WARNING **: Unhandled action type (nil)

(emerald:7533): Wnck-WARNING **: Unhandled action type (nil)

(emerald:7533): Wnck-WARNING **: Unhandled action type (nil)

---

### Post by Forlong on 2007-10-01
There's no error message regarding any plugins.
Start a new profile and see if it helps.

---

### Post by kris2pe on 2007-10-01
Solve by disabling emerald--replace!
How do I make the genie effect work! 
I tried enabling it doesn't seem to work!

---

### Post by Linicks on 2007-10-01
Thanks Forlong!  Great how to, and being lucky, no real issues here.

I really liked the default mini-install of compiz that comes with the UK Dell pre-installed Ubuntu on the Inspiron 6400.  I always thought it was a bit of a gimmick, but after using it for a few minutes, WOW.  I can't do without it now.

The compiz-fusion build is even more WOW... unbelievable.

Nick (too!) :-D

---

### Post by Forlong on 2007-10-01
> **kris2pe said:**
> How do I make the genie effect work!
You mean the minimizing animation? Choose magic lamp in the animations settings (see the set up guide how to do that).
> **kris2pe said:**
> I tried enabling it doesn't seem to work!
Could you please try to be more specific. Didn't the effect change at all or are you not happy with the result?


To Nick (haha, weird to address someone of the same name :D): I'm glad that it worked for you and I really appreciate having such comments here once in a while. :)

---

### Post by kris2pe on 2007-10-01
> **Forlong said:**
> You mean the minimizing animation? Choose magic lamp in the animations settings (see the set up guide how to do that).
I already enabled the genie effect! No its not written in the guide!
> **Forlong said:**
> 
Could you please try to be more specific. Didn't the effect change at all or are you not happy with the result?
The didn't appear it still the minimize effect where the window scales down until it closes down.

---

### Post by Forlong on 2007-10-01
> **kris2pe said:**
> I already enabled the genie effect! No its not written in the guide!
Of course it's not *exactly* in the guide, just how you enable effects in general.

Here's a screenshot for reference how to set it and where:

[[IMG]http://img3.imagebanana.com/img/cwuvgxx0/thumb/magiclamp.png[/IMG]](http://img3.imagebanana.com/view/cwuvgxx0/magiclamp.png)

You also have to disable *Fading Windows*

---

### Post by kris2pe on 2007-10-01
> **Forlong said:**
> Of course it's not *exactly* in the guide, just how you enable effects in general.

Here's a screenshot for reference how to set it and where:

[[IMG]http://img3.imagebanana.com/img/cwuvgxx0/thumb/magiclamp.png[/IMG]](http://img3.imagebanana.com/view/cwuvgxx0/magiclamp.png)

You also have to disable *Fading Windows*

Is there a way to make this effect just like the Mac?
I also notice when I try some filters different,switching tabs on firefox seems to be slow!

---

### Post by Forlong on 2007-10-02
> **kris2pe said:**
> Is there a way to make this effect just like the Mac?
No, because Apple has a patent on this.
> **kris2pe said:**
> I also notice when I try some filters different,switching tabs on firefox seems to be slow!
Sorry, I can't confirm this here, so I don't know what you cloud do about this...

---

### Post by kris2pe on 2007-10-02
> **Forlong said:**
> No, because Apple has a patent on this.

Sorry, I can't confirm this here, so I don't know what you cloud do about this...

Thank anyways. I hear that there's a new version of compiz commin out!
[http://www.phoronix.com/scan.php?page=news_item&px=NjA4NA](http://www.phoronix.com/scan.php?page=news_item&px=NjA4NA)
Is this stable? How can I update it? Thanks

---

### Post by Forlong on 2007-10-02
> **kris2pe said:**
> I hear that there's a new version of compiz commin out!
[http://www.phoronix.com/scan.php?page=news_item&px=NjA4NA](http://www.phoronix.com/scan.php?page=news_item&px=NjA4NA)
Is this stable? How can I update it? Thanks
The version you are using right now, is in fact a snapshot of this version, so you are using Compiz 0.6 pretty much already. :)

---

### Post by Saosin on 2007-10-03
hey!

kris2pe 

i think i have the same problem than you, how do you disable emerald??

thx

---

### Post by Forlong on 2007-10-03
> **Saosin said:**
> how do you disable emerald??
Just remove it:
```
sudo apt-get remove emerald && sudo apt-get autoremove
```

---

### Post by TimVB on 2007-10-05
Forlong, you seem to be doing a sterling effort helping us all!  And with lots of patience too...

The HowTo was great, but unfortunately on my system nothing happens when I try to 'compiz --replace' or 'emerald --replace'.  The problem may be due to an ATI graphics card, namely:

```
tim@tim-laptop:~$ lspci
...
01:00.0 VGA compatible controller: ATI Technologies Inc Radeon Mobility M6 LY
```

However, I was running a LinuxMint 3.0 Live CD last night on the same computer and Emerald seemed to work more-or-less fine.  

If I start System > Preferences > Emerald Theme Manager then nothing happens at all when I click on the various themes available.

I've tried editing xorg.conf and using both the "radeon" and "ati" driver, with no success.  If it helps, the output from running 'compiz --replace' in terminal is:

```
tim@tim-laptop:~$ compiz --replace
Checking for Xgl: not present. 
Detected PCI ID for VGA: 01:00.0 0300: 1002:4c59 (prog-if 00 [VGA])
Checking for texture_from_pixmap: not present. 
Trying again with indirect rendering:
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
Comparing resolution (1024x768) to maximum 3D texture size (512): Failed.
aborting and using fallback: /usr/bin/metacity 
Window manager warning: "" found in configuration database is not a valid value for keybinding "toggle_shaded"
```

Any ideas??

---

### Post by Forlong on 2007-10-05
> **TimVB said:**
> ```
01:00.0 VGA compatible controller: ATI Technologies Inc Radeon Mobility M6 LY
```

However, I was running a LinuxMint 3.0 Live CD last night on the same computer and Emerald seemed to work more-or-less fine.
I had someone in the german Ubuntu forum with that card lately.
We didn't get Compiz Fusion to work but we tried Beryl in the end and it worked. So I assume Mint uses Beryl by default.

I have no idea why it didn't work with Compiz and the guy didn't try again since for obvious reasons.

All I can tell you is this: you have to use the open radeon driver, because ATI does not support this card anymore ("ati" or "radeon" in the xorg.conf won't make any difference, because the ati driver makes use of radeon).


Anyway... try this in the terminal:
```
SKIP_CHECKS=yes compiz
```

---

### Post by TimVB on 2007-10-05
> **Forlong said:**
> I had someone in the german Ubuntu forum with that card lately.
We didn't get Compiz Fusion to work but we tried Beryl in the end and it worked. So I assume Mint uses Beryl by default.

I have no idea why it didn't work with Compiz and the guy didn't try again since for obvious reasons.

All I can tell you is this: you have to use the open radeon driver, because ATI does not support this card anymore ("ati" or "radeon" in the xorg.conf won't make any difference, because the ati driver makes use of radeon).


Anyway... try this in the terminal:
```
SKIP_CHECKS=yes compiz
```

Ah yes, now you mention it - perhaps it was Beryl.  My mistake.  I did what you suggested, and it worked!  It was kinda buggy (e.g. white featureless borders when windows were maximised, and my auto-hide panels don't come out on top when they slide out) but these may be more to do with Compiz and it's settings than HOWTO install CF.  (But any hints gratefully received nonetheless :) )

If it's of value, here is the output from the terminal (edited for brevity)

```
tim@tim-laptop:~$ SKIP_CHECKS=yes compiz
Checking for Xgl: not present. 
Detected PCI ID for VGA: 01:00.0 0300: 1002:4c59 (prog-if 00 [VGA])
Checking for texture_from_pixmap: not present. 
Trying again with indirect rendering:
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
Comparing resolution (1024x768) to maximum 3D texture size (512): Failed.
SKIP_CHECKS is yes, so continuing despite problems.
Checking for nVidia: not present. 
Checking for FBConfig: present. 
Checking for Xgl: not present. 
Starting emerald

(emerald:12399): Wnck-WARNING **: Unhandled action type (nil)

*These lines appeared many many times*

(emerald:12399): Wnck-WARNING **: Unhandled action type (nil)

(emerald:12399): Wnck-WARNING **: Unhandled action type (nil)
Attempted to unregister path (path[0] = org path[1] = freedesktop) which isn't registered
Attempted to unregister path (path[0] = org path[1] = freedesktop) which isn't registered

*Lots and lots of these lines as well*

Attempted to unregister path (path[0] = org path[1] = freedesktop) which isn't registered
A handler is already registered for the path starting with path[0] = "org"

A handler is already registered for the path starting with path[0] = "org"

(emerald:12399): Wnck-WARNING **: Unhandled action type (nil)
*And a few more of these*
(emerald:12399): Wnck-WARNING **: Unhandled action type (nil)

```

If there's anything you can usefully  help me with, I'd love to know.  E.g. what's the best way to remove CF and install Beryl (and is it recommended or not), or how to fix the 'buggy-ness' I mentioned above.  Otherwise I'll search some more appropriate forums and keep saving the pennies to get a new computer!

Thanks!

---

### Post by Forlong on 2007-10-05
Please post the output of
```
grep -v ^# /etc/X11/xorg.conf
```

---

### Post by TimVB on 2007-10-05
> **Forlong said:**
> Please post the output of
```
grep -v ^# /etc/X11/xorg.conf
```

Here it is.  I'm not running CF at the moment, if that makes a difference.

```
tim@tim-laptop:~$ grep -v ^# /etc/X11/xorg.conf

Section "Files"
        FontPath        "/usr/share/fonts/X11/misc"
        FontPath        "/usr/share/fonts/X11/cyrillic"
        FontPath        "/usr/share/fonts/X11/100dpi/:unscaled"
        FontPath        "/usr/share/fonts/X11/75dpi/:unscaled"
        FontPath        "/usr/share/fonts/X11/Type1"
        FontPath        "/usr/share/fonts/X11/100dpi"
        FontPath        "/usr/share/fonts/X11/75dpi"
        # path to defoma fonts
        FontPath        "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
        Load    "i2c"
        Load    "bitmap"
        Load    "ddc"
        Load    "dri"
        Load    "extmod"
        Load    "freetype"
        Load    "glx"
        Load    "int10"
        Load    "vbe"
EndSection

Section "InputDevice"
        Identifier      "Generic Keyboard"
        Driver          "kbd"
        Option          "CoreKeyboard"
        Option          "XkbRules"      "xorg"
        Option          "XkbModel"      "pc105"
        Option          "XkbLayout"     "gb"
EndSection

Section "InputDevice"
        Identifier      "Configured Mouse"
        Driver          "mouse"
        Option          "CorePointer"
        Option          "Device"                "/dev/input/mice"
        Option          "Protocol"              "ImPS/2"
        Option          "ZAxisMapping"          "4 5"
        Option          "Emulate3Buttons"       "true"
EndSection

Section "InputDevice"
        Driver          "wacom"
        Identifier      "stylus"
        Option          "Device"        "/dev/input/wacom"
        Option          "Type"          "stylus"
        Option          "ForceDevice"   "ISDV4"         # Tablet PC ONLY
EndSection

Section "InputDevice"
        Driver          "wacom"
        Identifier      "eraser"
        Option          "Device"        "/dev/input/wacom"
        Option          "Type"          "eraser"
        Option          "ForceDevice"   "ISDV4"         # Tablet PC ONLY
EndSection

Section "InputDevice"
        Driver          "wacom"
        Identifier      "cursor"
        Option          "Device"        "/dev/input/wacom"
        Option          "Type"          "cursor"
        Option          "ForceDevice"   "ISDV4"         # Tablet PC ONLY
EndSection

Section "Device"
        Identifier      "ATI Technologies Inc Radeon Mobility M6 LY"
        Driver          "ati"
        BusID           "PCI:1:0:0"
EndSection

Section "Monitor"
        Identifier      "Generic Monitor"
        Option          "DPMS"
        HorizSync       28-51
        VertRefresh     43-60
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Device          "ATI Technologies Inc Radeon Mobility M6 LY"
        Monitor         "Generic Monitor"
        DefaultDepth    24
        SubSection "Display"
                Depth           1
                Modes           "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           4
                Modes           "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           8
                Modes           "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           15
                Modes           "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           16
                Modes           "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           24
                Modes           "1024x768" "800x600" "640x480"
        EndSubSection
EndSection

Section "ServerLayout"
        Identifier      "Default Layout"
        Screen          "Default Screen"
        InputDevice     "Generic Keyboard"
        InputDevice     "Configured Mouse"
        InputDevice     "stylus"        "SendCoreEvents"
        InputDevice     "cursor"        "SendCoreEvents"
        InputDevice     "eraser"        "SendCoreEvents"
EndSection

Section "DRI"
        Mode    0666
EndSection
tim@tim-laptop:~$ 
```

---

### Post by dynamethod on 2007-10-05
i got this when i got to the press alt F2 and enter compiz --replace stage:

Checking for Xgl: not present. 
No whitelisted driver found
aborting and using fallback: /usr/bin/metacity 


what happend?

---

### Post by Forlong on 2007-10-05
@TimVB: Try adding this to the *Section "Device"*:
```
    Option "XAANoOffscreenPixmaps" "true"
```
You have to open your xorg.conf being root like this:
```
sudo gedit /etc/X11/xorg.conf
```


@dynamethod: What graphics card and what driver are you using for that?

---

### Post by TimVB on 2007-10-06
(A reminder if anyone is trying to follow along: I'm trying to get CF working on my laptop which has an ATI Radeon Mobility M6 LY graphics card.)

[QUOTE=Forlong;3481420]@TimVB: Try adding this to the *Section "Device"*:
```
    Option "XAANoOffscreenPixmaps" "true"
```
/QUOTE]

I did this, so the relevant section from xorg.conf reads:

```
Section "Device"
	Identifier	"ATI Technologies Inc Radeon Mobility M6 LY"
	Driver		"ati"
	BusID		"PCI:1:0:0"
    	Option 		"XAANoOffscreenPixmaps" "true"
EndSection

```

There was no noticeable difference.  Running "SKIP_CHECKS=yes compiz" or "SKIP_CHECKS=yes emerald" didn't seem to do anything different from before adding the line you suggested.  I've attached a screenshot so you can see what I mean about maximised windows having a white border; no icons are visible although (thankfully) if I hover over the invisible icon I do at least get a tooltip saying what the icon is, so I can restore the window to its original size.

I ran the LinuxMint 3.0 LiveCD again (as mentioned above) and can confirm that it uses Beryl, and seems a bit more stable than CF running in Feisty.  But it also has the problem with maximised windows having a white featureless border.  I don't honestly mind if you say "it's a hardware problem, that's life" because I'm planning on getting a ubuntu-friendlier computer quite soon anyway!

---

### Post by Forlong on 2007-10-06
> **TimVB said:**
> I don't honestly mind if you say "it's a hardware problem, that's life" because I'm planning on getting a ubuntu-friendlier computer quite soon anyway!
Well, I wouldn't have said it this way... ;)

It's certainly better to wait with Compiz for the new computer. Gutsy will have Compiz Fusion installed by default anyway, so you won't need no crappy guide anymore then. :)

---

### Post by TimVB on 2007-10-06
Forlong, thanks for all the help.  I'm sure it's been said before - but people like you make Ubuntu Forums a happy place to be looking for advice.  

Tim

---

### Post by diamondnular on 2007-10-06
> **diamondnular said:**
> Yes, I checked that. No helps at all. :(

Now I manage to have it "somewhat" worked by Alt - F2 and type "compiz --replace --indirect-rendering. I said "somewhat" because it still has another problems. Now I do not have "black screen with top bar", but instead, I usually have "white" or "freeze" windows. Anybody experiences the same issue?

Thanks,

KC.

Problem solved. Just update the driver to the latest one (100.14.19) and everything works just fine, with the default setup.

KC.

---

### Post by b-rose on 2007-10-06
Ok guys. I walked through this setup to the word. When I set up xgl to run and select it from the log in screen, I log in and it shows a black and white tv snow like background and a black x in the middle of the screen for a second before it loads up normally. I can access the Compiz Settings and select stuff and everything, but nothing works. No freezing or anything like that, but nothing works. Any ideas?

---

### Post by Forlong on 2007-10-07
Sounds good so far.
What output gives ```
compiz
``` in the terminal?

---

### Post by Norrbagge on 2007-10-07
i am gonna give this another go now... But a question i have not seen an answer too is. It says in the guide that i have to remove everything related to compiz, beryl and emerald. Except what came with the Ubuntu installation. How do i know what came with the installation???

also in my synaptic i have two options when removing. Do i have to just "remove", or "permanently remove"???

sorry if i have overseen this looking through the thread. I have also searched for this answer, but havent seen it...

BTW: will it be a problem having Kiba-Dock installed when using your guide???

---

### Post by Forlong on 2007-10-07
> **Norrbagge said:**
> It says in the guide that i have to remove everything related to compiz, beryl and emerald. Except what came with the Ubuntu installation. How do i know what came with the installation???
No, there's no exception in the guide. Remove everything related to Compiz, Beryl and Emerald. Period.
> **Norrbagge said:**
> also in my synaptic i have two options when removing. Do i have to just "remove", or "permanently remove"???
Whatever suits you best. Complete removal is better but not necessary.
> **Norrbagge said:**
> will it be a problem having Kiba-Dock installed when using your guide???
No.

---

### Post by Norrbagge on 2007-10-07
ok... thanks for clearing that up for me... head first into it i go, hoping i get out alive...):P

---

### Post by ashinshanghai on 2007-10-07
Forlong:

Thanks not only for your great installation guide (like a charm), but also for your remarkable patience in following up on all these posts.

I am a total noobie to linux, and this was the simplest install I've done yet (and I love my new look). However, after getting Compiz Fusion up and running, I am now having problems with AmoraK and KTorrent. I keep getting pop-up messages (from both apps) that say:

"Cannot talk to klauncher"

I notice that the icon for Amorak that usually sits in the system tray upon minimization now just kind of hovers in space on the desktop. 

This is more annoying really than anything problematic, but it means I can't pull up Amorak on the current desktop, and I can't open torrent files directly from the current desktop either.

Thoughts anyone?

---

### Post by Norrbagge on 2007-10-07
After adding the APT line in synaptic as written in the guide i got this error:

[http://ppa.launchpad.net/amaranth/ubuntu/dists/feisty/main/binary-i386/Packages.gz:](http://ppa.launchpad.net/amaranth/ubuntu/dists/feisty/main/binary-i386/Packages.gz:) Underprosessen gzip ga en feilkode (1)

 Underprosessen gzip ga en feilkode (1): Underprocess gave an error

---

### Post by Forlong on 2007-10-07
> **ashinshanghai said:**
> "Cannot talk to klauncher"
Try this:
```
dcopserver_shutdown
```
And then that:
```
kdeinit
```


> **Norrbagge said:**
> Underprosessen gzip ga en feilkode (1): Underprocess gave an error
Yeah, **gzip** gave an error. That means the error message is related to that.

---

### Post by Norrbagge on 2007-10-07
now i solved it... it didnt help to uninstall Gzip... i tried it and rebooted to be on the safe side... After much wasted time i manually edited it, and somehow it worked... Dont ask me why cause i dont know. but i dont moan cause i managed to install it...

ANYWHO. its now up and running and i am happy8-)

Thanks a million Forlong for your job and for bearing with me and helping me;-)

---

### Post by ashinshanghai on 2007-10-07
Hey, that worked nice! Thanks for the third time.

---

### Post by ashinshanghai on 2007-10-07
Hmmm, another issue. 

After installing Compiz Fusion, my video players are not working properly (both Movie Player and VLC). Audio is fine, but the video just displays a blank screen.

---

### Post by darkness5723 on 2007-10-07
hmm this is an interesting problem. I have compiz-fusion running perfectly on my desktop and I successfully got it working on my friend's computer as well. 
Now.. I went to install it on my laptop using your method forlong. After much tinkering I figured out the problem was emerald and not compiz. Compiz works beautifully... however whenever Emerald tries to start it crashes instantly and spits a whole bunch of stuff out of the terminal. Compiz without a window decorator isn't the same.. any fixes for this?

---

### Post by Forlong on 2007-10-08
> **ashinshanghai said:**
> After installing Compiz Fusion, my video players are not working properly (both Movie Player and VLC). Audio is fine, but the video just displays a blank screen.
Run ```
gstreamer-properties
```
then go to *Video &#8594; Default Output &#8594; Plugin* and set it to **X Window System (No Xv)**


> **darkness5723 said:**
> whenever Emerald tries to start it crashes instantly and spits a whole bunch of stuff out of the terminal.
Could you post that here - use the forum's CODE tag please (# button)

---

### Post by ashinshanghai on 2007-10-08
> **Forlong said:**
> Run ```
gstreamer-properties
```
then go to *Video &#8594; Default Output &#8594; Plugin* and set it to **X Window System (No Xv)**


It works, but very pixelated.

---

### Post by Forlong on 2007-10-08
Works fine here. Maybe this can help you out: [http://wiki.compiz-fusion.org/VideoPlayback](http://wiki.compiz-fusion.org/VideoPlayback)

---

### Post by flarkit on 2007-10-13
Hi

Just a quick word of thanks... your guide was clear enough for a semi-technical person like me to follow. At first it seemed as if the "CTRL+ALT+mouse" wasn't working, but it's mysteriously working now. Video playback is perfect with both Movie Player and VLC, so I'm really grateful for your efforts.

:)
:KS

---

### Post by White Stacey on 2007-10-15
i've used ur tut and got compiz fusion up and running except i have a couple issues that were not disscussed in this thread. First, after i install ubuntu7.04 there is 125 updates that can be applied, should i apply them?and if so at what step?and secondly, its like my desktop is too big vertically and i am required to scroll up and down to get to either tool bar, but there is no scroll bar.how do i reduce my verticle resolution?

---

### Post by Forlong on 2007-10-15
> **White Stacey said:**
> First, after i install ubuntu7.04 there is 125 updates that can be applied, should i apply them?
Yes, of course. Feitsy came out 6 months ago.
> **White Stacey said:**
> and if so at what step?
Right after the install. That's the first thing to do.
> **White Stacey said:**
> and secondly, its like my desktop is too big vertically and i am required to scroll up and down to get to either tool bar, but there is no scroll bar.how do i reduce my verticle resolution?
Post the output of
```
grep -v ^# /etc/X11/xorg.conf
```
and use the forum's CODE tag please (# button)

---

### Post by White Stacey on 2007-10-15
[QUOTEPost the output of
```
grep -v ^# /etc/X11/xorg.conf
```/QUOTE]

in terminal?

[QUOTEand use the forum's CODE tag please (# button)[/QUOTE]

whats a code tag?

sorry about the newb qestions,im really new to this

---

### Post by Forlong on 2007-10-15
> **White Stacey said:**
> in terminal?
Yes, please.
> **White Stacey said:**
> whats a code tag?
Just copy & paste the output, select it and click on this button: [http://ubuntuforums.org/attachment.php?attachmentid=46220&d=1192297804](http://ubuntuforums.org/attachment.php?attachmentid=46220&d=1192297804)

---

### Post by White Stacey on 2007-10-15
grep -v ^# /etc/X11/xorg.conf

        Option          "DPMS"
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Device          "nVidia Corporation G71 [GeForce 7300 GS]"
        Monitor         "W2306C"
        Defaultdepth    24
        SubSection "Display"
                Depth   1
                Modes           "1360x768"      "1280x1024"     "1024x768"     "832x624"        "800x600"       "720x400"       "640x480"
        EndSubSection
        SubSection "Display"
                Depth   4
                Modes           "1360x768"      "1280x1024"     "1024x768"     "832x624"        "800x600"       "720x400"       "640x480"
        EndSubSection
        SubSection "Display"
                Depth   8
                Modes           "1360x768"      "1280x1024"     "1024x768"     "832x624"        "800x600"       "720x400"       "640x480"
        EndSubSection
        SubSection "Display"
                Depth   15
                Modes           "1360x768"      "1280x1024"     "1024x768"     "832x624"        "800x600"       "720x400"       "640x480"
        EndSubSection
        SubSection "Display"
                Depth   16
                Modes           "1360x768"      "1280x1024"     "1024x768"     "832x624"        "800x600"       "720x400"       "640x480"
        EndSubSection
        SubSection "Display"
                Depth   24
                Modes           "1360x768"      "1280x1024"     "1024x768"     "832x624"        "800x600"       "720x400"       "640x480"
        EndSubSection
EndSection

Section "ServerLayout"
        Identifier      "Default Layout"
  screen "Default Screen"
        Inputdevice     "Generic Keyboard"
        Inputdevice     "Configured Mouse"
        Inputdevice     "stylus"        "SendCoreEvents"
        Inputdevice     "cursor"        "SendCoreEvents"
        Inputdevice     "eraser"        "SendCoreEvents"
EndSection

Section "DRI"
        Mode    0666
EndSection



---

### Post by Forlong on 2007-10-15
If that's really the complete ouput, I recommend resetting your xorg conf.
Do a backup first:
```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.bak
```
Then:
```
sudo dpkg-reconfigure xserver-xorg
```
And afterwrds:
```
sudo nvidia-xconfig --add-argb-glx-visuals -d 24
```
Finally reboot and see if it worked.

---

### Post by White Stacey on 2007-10-16
i had compiz up and running two days ago but i formatted my drive to do it over and now compiz wont start. i follow the same steps as your guide suggests, exactly the same every time. What am i doing wrong this time? As well theres something wrong with my video card driver. as i described previously,my desktop is too big vertically.** i tried your suggestion of resetting the xorg, with no success**. my resolution is fine throughout the ubuntu install,update and compiz install.until i install nvidia driver, thats when the resolution changes. please help.
__________________

---

### Post by tomi_hl on 2007-10-16
When i tried to run "compiz --replace" I got following messase
```
Checking for Xgl: not present. 
Blacklisted PCIID '8086:2a02' found 
aborting and using fallback: /usr/bin/metacity 
Window manager warning: "" found in configuration database is not a valid value for keybinding "toggle_shaded"

```

here's my lspci output
```
00:00.0 Host bridge: Intel Corporation Mobile Memory Controller Hub (rev 0c)
00:02.0 VGA compatible controller: Intel Corporation Mobile Integrated Graphics Controller (rev 0c)
00:02.1 Display controller: Intel Corporation Mobile Integrated Graphics Controller (rev 0c)
00:1a.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI #4 (rev 03)
00:1a.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI #5 (rev 03)
00:1a.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI #2 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 03)
00:1c.1 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 2 (rev 03)
00:1c.2 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 3 (rev 03)
00:1c.4 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 5 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI #3 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev f3)
00:1f.0 ISA bridge: Intel Corporation Mobile LPC Interface Controller (rev 03)
00:1f.1 IDE interface: Intel Corporation Mobile IDE Controller (rev 03)
00:1f.2 SATA controller: Intel Corporation Mobile SATA AHCI Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 03)
06:00.0 Network controller: Intel Corporation Unknown device 4229 (rev 61)
08:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8036 PCI-E Fast Ethernet Controller (rev 16)
09:03.0 CardBus bridge: Texas Instruments PCIxx12 Cardbus Controller
09:03.1 FireWire (IEEE 1394): Texas Instruments PCIxx12 OHCI Compliant IEEE 1394 Host Controller
09:03.2 Mass storage controller: Texas Instruments 5-in-1 Multimedia Card Reader (SD/MMC/MS/MS PRO/xD)

```

and my xorg.conf
```
# /etc/X11/xorg.conf (xorg X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the xorg.conf(5) manual page.
# (Type "man xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "Files"
	FontPath	"/usr/share/fonts/X11/misc"
	FontPath	"/usr/share/fonts/X11/cyrillic"
	FontPath	"/usr/share/fonts/X11/100dpi/:unscaled"
	FontPath	"/usr/share/fonts/X11/75dpi/:unscaled"
	FontPath	"/usr/share/fonts/X11/Type1"
	FontPath	"/usr/share/fonts/X11/100dpi"
	FontPath	"/usr/share/fonts/X11/75dpi"
	# path to defoma fonts
	FontPath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
	Load	"i2c"
	Load	"bitmap"
	Load	"ddc"
	Load	"dri"
	Load	"extmod"
	Load	"freetype"
	Load	"glx"
	Load	"int10"
	Load	"vbe"
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"us"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"		"/dev/input/mice"
	Option		"Protocol"		"ImPS/2"
	Option		"ZAxisMapping"		"4 5"
	Option		"Emulate3Buttons"	"true"
EndSection

Section "InputDevice"
	Identifier	"Synaptics Touchpad"
	Driver		"synaptics"
	Option		"SendCoreEvents"	"true"
	Option		"Device"		"/dev/psaux"
	Option		"Protocol"		"auto-dev"
	Option		"HorizScrollDelta"	"0"
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"stylus"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"		"stylus"
	Option		"ForceDevice"	"ISDV4"		# Tablet PC ONLY
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"eraser"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"		"eraser"
	Option		"ForceDevice"	"ISDV4"		# Tablet PC ONLY
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"cursor"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"		"cursor"
	Option		"ForceDevice"	"ISDV4"		# Tablet PC ONLY
EndSection

Section "Device"
	Identifier	"Generic Video Card"
	Driver		"intel"
	BusID		"PCI:0:2:0"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Generic Video Card"
	Monitor		"Generic Monitor"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		 "800x600" "1024x768" "1280x800"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		 "800x600" "1024x768" "1280x800"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		 "800x600" "1024x768" "1280x800"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		 "800x600" "1024x768" "1280x800"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		 "800x600" "1024x768" "1280x800"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		 "800x600" "1024x768" "1280x800" 
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
	InputDevice     "stylus"	"SendCoreEvents"
	InputDevice     "cursor"	"SendCoreEvents"
	InputDevice     "eraser"	"SendCoreEvents"
	InputDevice	"Synaptics Touchpad"
EndSection

Section "DRI"
	Mode	0666
EndSection

Section "Extensions"
         Option "Composite" "Disable"
EndSection
```

I tried commenting the blacklisted pciid in /usr/bin/compiz and here's what i got
```
Checking for Xgl: not present. 
Detected PCI ID for VGA: 00:02.0 0300: 8086:2a02 (rev 0c) (prog-if 00 [VGA])
Checking for texture_from_pixmap: not present. 
Trying again with indirect rendering:
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: not present. 
aborting and using fallback: /usr/bin/metacity 
Window manager warning: "" found in configuration database is not a valid value for keybinding "toggle_shaded"
```


please help.

thanks

---

### Post by dexjul on 2007-10-16
Hi,

I got this error:

dexter@dexter-laptop:~$ compiz --replace
Checking for Xgl: not present. 
Checking for texture_from_pixmap: not present. 
Trying again with indirect rendering:
Checking for texture_from_pixmap: not present. 
aborting and using fallback: /usr/bin/metacity 

I already installed 

sudo apt-get install xserver-xgl

sudo apt-get install xorg-driver-fglrx


and added this to xorg.conf

Section "Device"
        Identifier      "Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller"
        Driver          "i810"
        BusID           "PCI:0:2:0"
        Option          "XAANoOffscreenPixmaps" "true"
EndSection

Thanks...

---

### Post by Forlong on 2007-10-17
> **tomi_hl said:**
> ```
 Checking for Composite extension: not present.
```
You have composite disabled in your xorg.conf.
Change this
```
Section "Extensions"
         Option "Composite" "Disable"
EndSection
```
to
```
Section "Extensions"
         Option "Composite" "Enable"
EndSection
```


@dexjul: you do not need Xgl with an intel card. Check this out: [http://wiki.compiz-fusion.org/Intel_with_AiGLX](http://wiki.compiz-fusion.org/Intel_with_AiGLX)
Hope it helps.

---

### Post by Adam590 on 2007-10-18
Forlong, many thanks for the great guide!

I've got everything working perfectly - just having a little trouble getting Emerald to load along with Compiz at startup. I removed **compiz-gnome**, created the startscript, changed its permission to "Allow executing file as program", and inserted *emerald* as a Window Decoration command.

So how do I use the startscript? I already had a startup program named *compiz* with the command *compiz --replace* from a previous step in your guide. That one worked fine. I tried changing its command to *start-compiz* (the name of the startscript), but no go. Then I changed it to *start-compiz --replace*, and then to the full address of the file, but still no go.

After that, I tried fooling around with the startscript's other permissions, so I'm including a picture of them, in case that helps.


Note: using Alt+F2 to run *emerald --replace* does what it should - just hoping I can get it at startup.

---

### Post by Forlong on 2007-10-18
Forget about the script. I didn't update the guide there.
Now /usr/bin/compiz "favours" Emerald over gtk-window-decorator (it was the other way around before)
So if you are running compiz, Emerald should automatically start with it.

If that's not the case, post the output of
```
compiz
``` in terminal.

---

### Post by xcafeus on 2007-10-18
I just finished reinstalling Gutsy to my laptop (my previous installation wnet bad due to -probably my bad handling- of compiz. So now I thought I should ask you guys... when I type compiz in the terminal I get:

george@laptop:~$ compiz
Checking for Xgl: not present. 
Blacklisted PCIID '8086:2a02' found 
aborting and using fallback: /usr/bin/metacity

Last time I installed Xgl and finally messed up the installation. I read that Intel (965) does not need Xgl... what should I do Im a bit lost. Also I had to install CCMS since I was not there after the installation of Gutsy...

any other info you guys might need please ask me to provide it...

---

### Post by Forlong on 2007-10-18
Try running Compiz lke this:
```
SKIP_CHECKS=yes compiz
```

---

### Post by xcafeus on 2007-10-18
> **Forlong said:**
> Try running Compiz lke this:
```
SKIP_CHECKS=yes compiz
```

I tried that and all windows "crashed"... could not move them around and Maximize, Close buttons disappeared. Also I got this:

george@laptop:~$ SKIP_CHECKS=yes compiz
Checking for Xgl: not present. 
Blacklisted PCIID '8086:2a02' found 
SKIP_CHECKS is yes, so continuing despite problems.
Checking for texture_from_pixmap: not present. 
Trying again with indirect rendering:
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
Comparing resolution (1280x800) to maximum 3D texture size (2048): Passed.
Checking for nVidia: not present. 
Checking for FBConfig: present. 
Checking for Xgl: not present. 
Starting gtk-window-decorator
/usr/bin/compiz.real (video) - Warn: No 8 bit GLX pixmap format, disabling YV12 image format
.......

doesnt look good...

EDIT: I had to ctrl+alt+backspace to get back to normal..

---

### Post by Adam590 on 2007-10-18
Here is the output of *compiz*:
```

$ compiz
Checking for Xgl: not present. 
Detected PCI ID for VGA: 01:00.0 0300: 10de:0324 (rev a1) (prog-if 00 [VGA])
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
Comparing resolution (1152x768) to maximum 3D texture size (4096): Passed.
Checking for nVidia: present. 
Checking for FBConfig: present. 
Checking for Xgl: not present. 
Starting emerald

(emerald:7223): Wnck-WARNING **: Unhandled action type (nil)

(emerald:7223): Wnck-WARNING **: Unhandled action type (nil)

(emerald:7223): Wnck-WARNING **: Unhandled action type (nil)

(emerald:7223): Wnck-WARNING **: Unhandled action type (nil)

(emerald:7223): Wnck-WARNING **: Unhandled action type (nil)

(emerald:7223): Wnck-WARNING **: Unhandled action type (nil)

(emerald:7223): Wnck-WARNING **: Unhandled action type (nil)

(emerald:7223): Wnck-WARNING **: Unhandled action type (nil)

(emerald:7223): Wnck-WARNING **: Unhandled action type (nil)

(emerald:7223): Wnck-WARNING **: Unhandled action type (nil)

(emerald:7223): Wnck-WARNING **: Unhandled action type (nil)

(emerald:7223): Wnck-WARNING **: Unhandled action type (nil)

(emerald:7223): Wnck-WARNING **: Unhandled action type (nil)

(emerald:7223): Wnck-WARNING **: Unhandled action type (nil)

(emerald:7223): Wnck-WARNING **: Unhandled action type (nil)

(emerald:7223): Wnck-WARNING **: Unhandled action type (nil)

(emerald:7223): Wnck-WARNING **: Unhandled action type (nil)

(emerald:7223): Wnck-WARNING **: Unhandled action type (nil)

(emerald:7223): Wnck-WARNING **: Unhandled action type (nil)

(emerald:7223): Wnck-WARNING **: Unhandled action type (nil)

(emerald:7223): Wnck-WARNING **: Unhandled action type (nil)

(emerald:7223): Wnck-WARNING **: Unhandled action type (nil)

(emerald:7223): Wnck-WARNING **: Unhandled action type (nil)

(emerald:7223): Wnck-WARNING **: Unhandled action type (nil)

(emerald:7223): Wnck-WARNING **: Unhandled action type (nil)

(emerald:7223): Wnck-WARNING **: Unhandled action type (nil)

(emerald:7223): Wnck-WARNING **: Unhandled action type (nil)

(emerald:7223): Wnck-WARNING **: Unhandled action type (nil)

(emerald:7223): Wnck-WARNING **: Unhandled action type (nil)

(emerald:7223): Wnck-WARNING **: Unhandled action type (nil)
/usr/bin/compiz.real (video) - Warn: No 8 bit GLX pixmap format, disabling YV12 image format

```

You're right - it does seem to start emerald automatically. So do I need Xgl?
I've got an Nvidia GeForce FX Go5200, if that helps, but I thought my Nvidia drivers were all squared away...

---

### Post by Forlong on 2007-10-19
> **xcafeus said:**
> doesnt look good...
Yeah, I guess your graphics card is blacklisted for a reason. :(

> **Adam590 said:**
> You're right - it does seem to start emerald automatically.
It does, actually.
> **Adam590 said:**
> So do I need Xgl?
No, definitely not.
> **Adam590 said:**
> I've got an Nvidia GeForce FX Go5200
Try this in a terminal:
```
sudo nvidia-xconfig --add-argb-glx-visuals -d 24
```
(you have to restart X to make it work)

---

### Post by dexjul on 2007-10-19
Thank forlong.

Compiz is running now but same errors.

```
dexter@dexter-laptop:~$ LD_PRELOAD=/usr/lib/fglrx/libGL.so.1.2.xlibmesa compiz --replace
Checking for Xgl: not present. 
Checking for texture_from_pixmap: not present. 
Trying again with indirect rendering:
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
Checking for nVidia: not present. 
Checking for Xgl: not present. 

(gtk-window-decorator:5835): Wnck-WARNING **: Unhandled action type (nil)

(gtk-window-decorator:5835): Wnck-WARNING **: Unhandled action type (nil)

(gtk-window-decorator:5835): Wnck-WARNING **: Unhandled action type (nil)

(gtk-window-decorator:5835): Wnck-WARNING **: Unhandled action type (nil)

(gtk-window-decorator:5835): Wnck-WARNING **: Unhandled action type (nil)

(gtk-window-decorator:5835): Wnck-WARNING **: Unhandled action type (nil)

(gtk-window-decorator:5835): Wnck-WARNING **: Unhandled action type (nil)

(gtk-window-decorator:5835): Wnck-WARNING **: Unhandled action type (nil)

(gtk-window-decorator:5835): Wnck-WARNING **: Unhandled action type (nil)

(gtk-window-decorator:5835): Wnck-WARNING **: Unhandled action type (nil)
/usr/bin/compiz.real (video) - Warn: No 8 bit GLX pixmap format, disabling YV12 image format

(gtk-window-decorator:5835): Wnck-WARNING **: Unhandled action type (nil)

(gtk-window-decorator:5835): Wnck-WARNING **: Unhandled action type (nil)

(gtk-window-decorator:5835): Wnck-WARNING **: Unhandled action type (nil)

(gtk-window-decorator:5835): Wnck-WARNING **: Unhandled action type (nil)

(gtk-window-decorator:5835): Wnck-WARNING **: Unhandled action type (nil)

(gtk-window-decorator:5835): Wnck-WARNING **: Unhandled action type (nil)
/usr/bin/compiz.real (animation) - Debug: polygon.c: pset null at line 1455

/usr/bin/compiz.real (animation) - Debug: polygon.c: pset null at line 1455

/usr/bin/compiz.real (animation) - Debug: polygon.c: pset null at line 1455

/usr/bin/compiz.real (animation) - Debug: polygon.c: pset null at line 1455

/usr/bin/compiz.real (animation) - Debug: polygon.c: pset null at line 1455

/usr/bin/compiz.real (animation) - Debug: polygon.c: pset null at line 1455

/usr/bin/compiz.real (animation) - Debug: polygon.c: pset null at line 1455

```

Any idea how to fix this.

And Kindly explain this command

```
 LD_PRELOAD=/usr/lib/fglrx/libGL.so.1.2.xlibmesa compiz --replace

```

Thank you.

---

### Post by Adam590 on 2007-10-19
> **Forlong said:**
> Try this in a terminal:
```
sudo nvidia-xconfig --add-argb-glx-visuals -d 24
```
(you have to restart X to make it work)


Well, it inexplicably started working on its own.
Thanks, though - I've saved that command to try if things go south.

---

### Post by xcafeus on 2007-10-20
> **Forlong said:**
> Yeah, I guess your graphics card is blacklisted for a reason. :(



Its an Intel x3100 (chipset 965) which is supposed to be supported fully... I dont know I just wait ATM since I have other weird problems as well regarding FakeRAID and Gutsy. I hope gurus can sort it out because I surely cant. :guitar:

---

### Post by super-sauce on 2007-10-23
okay I installed compiz via your awesome guide btw, and this is what I get when I type ¨compiz¨ into the terminal:
infinity@ubuntu-brian:~$ compiz
Checking for Xgl: not present. 
Detected PCI ID for VGA: 01:00.0 0300: 10de:00f6 (rev a2) (prog-if 00 [VGA])
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: not present. 
aborting and using fallback: /usr/bin/metacity 

Any ideas on how to get compiz working?  I´ve tried using the 
*sudo nvidia-xconfig --add-argb-glx-visuals -d 24*
command but nothing.  I´m using an Nvidia GeForce 6800 XT agp 8x

Edit:
OH and I also tried using the skip checks command too and this is what it spit out:
infinity@ubuntu-brian:~$ SKIP_CHECKS=yes compiz
Checking for Xgl: not present. 
Detected PCI ID for VGA: 01:00.0 0300: 10de:00f6 (rev a2) (prog-if 00 [VGA])
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: not present. 
SKIP_CHECKS is yes, so continuing despite problems.
Checking for nVidia: present. 
Checking for FBConfig: present. 
Checking for Xgl: not present. 
Starting emerald

(emerald:5875): GLib-GObject-CRITICAL **: g_object_ref: assertion `G_IS_OBJECT (object)' failed
/usr/bin/compiz.real (core) - Fatal: No composite extension


2ND EDIT:
Okay I fixed the problem.  There was a line in my xorg.conf file that looked like this:
Section "Extensions"
    Option         "Composite"    ¨Disable¨
EndSection

All I did was erase ¨disable¨ saved the file, and restarted the x server, and now compiz works great.  Thanks for the awesome install guide.  For ppl having the same issue just type into terminal:
[COLOR="Navy"][COLOR="Navy"]gksudo gedit /ect/x11/xorg.conf[/COLOR][/COLOR]
scroll to the line mentioned above, and erase the ¨disable¨ next to your composite extension.  Save the file then simply logout and press ctrl+alt+backspace to restart the X server.

---

### Post by Forlong on 2007-10-25
Hi everybody,

sorry, I was very busy with universitym lately (and I participated in the [Ubucon](http://ubucon.de/) last weekend).
Please post again, if you still have any troubles.


Regards,
Nick

---

### Post by margaf77 on 2007-10-26
Hi and thanks for the guide. It installed with no issue following your directions. I have XGL installed and am using Feisty with an X1900 AIW with ATi's latest driver. I get none of the effects but I did get them to work with the compiz in the standard repos. Im hoping you can help a bit.

```
compiz --replace
Checking for Xgl: not present.
No whitelisted driver found
aborting and using fallback: /usr/bin/metacity
Window manager warning: "" found in configuration database is not a valid value for keybinding "toggle_shaded"

```

---

### Post by Forlong on 2007-10-26
Try to run Compiz like this:
```
SKIP_CHECKS=yes compiz
```
If it works, see the 12th step [here](http://forlong.blogage.de/article/2007/10/23/fglrx-8423---finally-with-AIGLX-support).

---

### Post by margaf77 on 2007-10-26
Here what I get now, its still not working.

```
Checking for Xgl: not present.
No whitelisted driver found
SKIP_CHECKS is yes, so continuing despite problems.
Checking for texture_from_pixmap: not present.
Trying again with indirect rendering:
Checking for texture_from_pixmap: present.
Checking for non power of two support: present.
Checking for Composite extension: present.
Comparing resolution (1280x1024) to maximum 3D texture size (4096): Passed.
Checking for nVidia: not present.
Checking for FBConfig: present.
Checking for Xgl: not present.
Starting emerald

(emerald:7870): Wnck-WARNING **: Unhandled action type (nil)

(emerald:7870): Wnck-WARNING **: Unhandled action type (nil)

(emerald:7870): Wnck-WARNING **: Unhandled action type (nil)

(emerald:7870): Wnck-WARNING **: Unhandled action type (nil)

(emerald:7870): Wnck-WARNING **: Unhandled action type (nil)

(emerald:7870): Wnck-WARNING **: Unhandled action type (nil)

(emerald:7870): Wnck-WARNING **: Unhandled action type (nil)

(emerald:7870): Wnck-WARNING **: Unhandled action type (nil)
/usr/bin/compiz.real (video) - Warn: No 8 bit GLX pixmap format, disabling YV12 image format
/usr/bin/compiz.real: symbol lookup error: /usr/lib/compiz/libdecoration.so: undefined symbol: decor_apply_gravity
Window manager warning: "" found in configuration database is not a valid value for keybinding "toggle_shaded"

```

---

### Post by ozzyprv on 2007-10-28
Hi Forlong,

I have been away from the forums for a while now, went to Europe for vacations!.

Are all the Compiz Fusion features included in Gusty Gibbon?

Thank you.

[COLOR="Red"]EDIT: Never mind, I found the answer - YES.[/COLOR]

---

### Post by dexjul on 2007-10-30
Hi, once again I having a problem in compiz fusion.

I follow forlong's blog, I got this errors.

```
dexter@dexter-laptop:~$ compiz --replace
Checking for Xgl: not present. 
Checking for texture_from_pixmap: not present. 
Trying again with indirect rendering:
Checking for texture_from_pixmap: not present. 
aborting and using fallback: /usr/bin/metacity 

```


```
dexter@dexter-laptop:~$ LD_PRELOAD=/usr/lib/fglrx/libGL.so.1.2.xlibmesa compiz --replace
Checking for Xgl: not present. 
Checking for texture_from_pixmap: not present. 
Trying again with indirect rendering:
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
Checking for nVidia: not present. 
Checking for Xgl: not present. 

(gtk-window-decorator:5789): Wnck-WARNING **: Unhandled action type (nil)

(gtk-window-decorator:5789): Wnck-WARNING **: Unhandled action type (nil)

(gtk-window-decorator:5789): Wnck-WARNING **: Unhandled action type (nil)

(gtk-window-decorator:5789): Wnck-WARNING **: Unhandled action type (nil)

(gtk-window-decorator:5789): Wnck-WARNING **: Unhandled action type (nil)

(gtk-window-decorator:5789): Wnck-WARNING **: Unhandled action type (nil)

(gtk-window-decorator:5789): Wnck-WARNING **: Unhandled action type (nil)

(gtk-window-decorator:5789): Wnck-WARNING **: Unhandled action type (nil)

(gtk-window-decorator:5789): Wnck-WARNING **: Unhandled action type (nil)

(gtk-window-decorator:5789): Wnck-WARNING **: Unhandled action type (nil)
/usr/bin/compiz.real: symbol lookup error: /usr/lib/compiz/libdecoration.so: undefined symbol: decor_apply_gravity

```

I already install 

```
sudo apt-get install xorg-driver-fglrx

```

then 

```
dexter@dexter-laptop:~$ fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: Tungsten Graphics, Inc
OpenGL renderer string: Mesa DRI Intel(R) 915GM 20061017 x86/MMX/SSE2
OpenGL version string: 1.3 Mesa 6.5.2

```


How to fix this problem. Thank you.

---

### Post by Forlong on 2007-10-30
> **dexjul said:**
> ```
dexter@dexter-laptop:~$ fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: Tungsten Graphics, Inc
OpenGL renderer string: Mesa DRI Intel(R) 915GM 20061017 x86/MMX/SSE2
OpenGL version string: 1.3 Mesa 6.5.2

```
The driver is not installed properly or your card isn't supported by it. What graphics card do you use?


You also seem to have issues with the installed Compiz packages. What's the output of ```
dpkg -l | grep compiz
```

---

### Post by dexjul on 2007-10-31
Here's the output


```
dexter@dexter-laptop:~$ dpkg -l | grep compiz
ii  compiz-core                                0.5.2-0ubuntu3~ppa4                    OpenGL window and compositing manager
ii  compiz-fusion-plugins-extra                0.5.2+git20070817-0ubuntu1~ppa1        Collection of extra plugins from OpenComposi
ii  compiz-fusion-plugins-main                 0.5.2-0ubuntu2~ppa1                    Collection of plugins from OpenCompositing f
ii  compiz-gnome                               0.5.2-0ubuntu3~ppa4                    OpenGL window and compositing manager - GNOM
rc  compiz-gtk                                 0.3.6-1ubuntu13                        OpenGL window and compositing manager - Gtk 
ii  compiz-plugins                             0.5.2-0ubuntu3~ppa4                    OpenGL window and compositing manager - plug
ii  compizconfig-settings-manager              0.5.2+git20070814-0ubuntu1~ppa1        Compiz configuration settings manager
ii  emerald                                    0.3~git20070717-0ubuntu1~ppa1          Decorator for compiz-fusion
ii  libcompizconfig-backend-gconf              0.5.2+git20070813-0ubuntu1~ppa1        Settings library for plugins - OpenCompositi
ii  libcompizconfig0                           0.5.2-0ubuntu1~ppa2                    Settings library for plugins - OpenCompositi
ii  libemeraldengine0                          0.3~git20070717-0ubuntu1~ppa1          Decoration engines for compiz-fusion
ii  python-compizconfig                        0.5.2-0ubuntu1~ppa1                    Compiz configuration system bindings
dexter@dexter-laptop:~$ 

```

---

### Post by dexjul on 2007-10-31
Here's my graphics card

Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller

Thanks for reply.

---

### Post by Bigdeath on 2007-10-31
I found that one of the easiest ways to get compiz fusion to work is to remove all instances of it and beryl,  rebuild your sources.list for gutsy here > [http://www.ubuntu-nl.org/source-o-matic/]("http://www.ubuntu-nl.org/source-o-matic/") , then upgrade to gutsy. If you got other repos in your software sources list you will download different versions of all this software and it breaks compiz fusion. I got it working this way then activated amaranths repo and upgraded compiz and I got the whick error again.

---

### Post by Forlong on 2007-10-31
@dexjul: fglrx is for ATI cards only. Remove it again:```

sudo apt-get remove xorg-driver-fglrx
```

In addition to that, if you disabled the repository (like I said in the guide) enable it again and see if there are any updates for you.

If you are still having troubles then, see if this can help you out: [http://wiki.compiz-fusion.org/Intel_with_AiGLX](http://wiki.compiz-fusion.org/Intel_with_AiGLX)


@Bigdeath: I'm not quite sure... are you still having issues or not?

---

### Post by Bigdeath on 2007-10-31
Sorry I didn't specify but it works just so long as I don't activate any other repos that cause compiz to upgrade to thier versions. As soon as I do that emerald no longer works as does any other windows decorator, and I get the whick error. But it works now.

---

### Post by Cariboo1938 on 2007-11-04
First I want to say thank you to 'Forlong' for making [The best way to install Compiz Fusion on Ubuntu Feisty"][URL="http://forlong.blogage.de/article/2007/10/2/Desktop-effects-by-default-in-Gutsy---how-Compiz-Fusion-enhances-Ubuntus-desktop-of-version-710"]THIS]("http://forlong.blogage.de/article/2007/8/26/The-best-way-to-install-Compiz-Fusion-on-Ubuntu-Feisty)[/URL] great guide.
I followed the instructions and when I tried to start Compiz in a terminal I got this message:
> Checking for Xgl: not present

I noticed some changes in the behavior of my desktop (see attached Screenshot with transparent window, showing the above mentioned message)
Because I'm absolutely new to this I do not know if I have to install Xgl to run compiz properly, or do I not have to install it? 
In the guide Xgl is only mentioned in connection to ATI users. 
I also learned that Xgl is not a final release and it might  not be fun at all to run it.
For any reply...Thanks in advance!

---

### Post by Forlong on 2007-11-05
No, with your graphics card you don't need Xgl.

The Compiz script just has to check any possibilities. If you want to know more about this, see [here](http://forlong.blogage.de/article/2007/10/2/Desktop-effects-by-default-in-Gutsy---how-Compiz-Fusion-enhances-Ubuntus-desktop-of-version-710).

---

### Post by Cariboo1938 on 2007-11-09
Hi all....Help please...
Which plugins do I have to enable in "CompizConfig Settings Manager" to get the cube?

---

### Post by Forlong on 2007-11-09
[How to set up Compiz Fusion](http://forlong.blogage.de/article/2007/8/29/How-to-set-up-Compiz-Fusion) &#8594; Getting the Cube

---

### Post by Cariboo1938 on 2007-11-09
Thank you for the immediate reply..
Two questions:
1) > Firstly, enable the following plugins (by checking the box next to them):
Do I have to uncheck all the default settings?

[B][COLOR="SeaGreen"]EDIT: OK, forget question 1)
When you check a plugin and there is a conflict, you will get a choice what to do. Fair enough.[/COLOR][/B]



2) What are the settings for these desktops: see attachment?

---

### Post by Forlong on 2007-11-10
> **Cariboo1938 said:**
> [B][COLOR="SeaGreen"]EDIT: OK, forget question 1)
When you check a plugin and there is a conflict, you will get a choice what to do. Fair enough.[/COLOR][/B]
Yes, that's what the guide says too:>  to actually use it, we might have to disable some other plugins (just follow the popup)
;)
> **Cariboo1938 said:**
> 2) What are the settings for these desktops: see attachment?
The first one is
> Cover Switch - if you enable the **Shift Switcher **this will be the default mode
And the second one:
> Flip 3D - choose **Flip** in **Shift Switcher &#8594; Switcher Mode**
Use [Super]+[Tab] to use them (with "Super" being the win-key).

---

### Post by tameek on 2007-11-10
> **Forlong said:**
> I updated the guides a little bit.
Added some icons and screenshots of the ring/shift switchers.
There's also a new transparency section in the [set-up entry](http://forlong.blogage.de/article/2007/8/29/How-to-set-up-Compiz-Fusion).

I hope you like it.


P.S.: as I noticed in my referral log, that my How-to got posted on [StumbleUpon](http://www.stumbleupon.com/url/forlong.blogage.de/article/2007/8/26/The-best-way-to-install-Compiz-Fusion-on-Ubuntu-Feisty) and [digg](http://digg.com/linux_unix/Install_stable_packages_for_Compiz_Fusion_on_Ubuntu_Feisty_for_beginners).
I'm really greatful for that, but please don't refer to the packages as stable. Although I said in the introduction, that these are the *most stable* ones you can get, you should keep in mind, there's not an official stable release yet.

Very Very helpful for a noob like me...you ROCK!:guitar:

---

### Post by reverend_HH on 2007-11-10
hey every1, i got compiz up and running..the only thing that i want is when i switch to a different desktop for my taskbar to only show the programs running in that desktop. almost seems to defeat the purpose of multiple desktops if ur taskbar is always cluttered. i gave kcontrol a look and found nothing, i thought i remember someone mentioning that i might need a plugin? not sure, plz help :)

---

### Post by Forlong on 2007-11-11
Sorry, I have very little knowledge about KDE, you may want to consider starting your own thread about that (although I'm sure it has already been discussed in the forums, try searching in this section)

Make sure you switched to the Flat-file Backend and try running Compiz like this:
```
compiz --ignore-desktop-hints
```

---

### Post by ozzyprv on 2007-11-23
Hey guys, I haven't been around this thread for weeks!.

I am having problem with my windows hiding behind my top taskbar.
Is there a way to stop the windows from going beyond the taskbar border?

Thanks.

---

### Post by Forlong on 2007-11-23
ccsm &#8594; Place Windows &#8594; Placement Mode &#8594; Smart

---

### Post by ozzyprv on 2007-11-25
> **Forlong said:**
> ccsm &#8594; Place Windows &#8594; Placement Mode &#8594; Smart

hmmm. Did not fix it.
Still, if for some reason I drag the window too hogh (or low) in the screen, the window border will go behind the taskbar.
I am attaching a screenshot of my desktop.

---

### Post by Forlong on 2007-11-25
You can get it back by holding [Alt] pressed and grabbing the window with the mouse.

I frankly don't know why this is happening to some people.

---

### Post by ozzyprv on 2007-11-25
This (Alt+grab) is good enough for now.

Is this solved in Gusty?

Thank you!.

---

### Post by Forlong on 2007-11-25
> **ozzyprv said:**
> Is this solved in Gusty?
At least for me... but then again, I never had a problem with this on Feisty either.

---

### Post by werewolfzx8 on 2007-11-27
Compiz was working fine for me up until today, now everything is loading real slow, and my titlebar keeps hiding behind my top taskbar. Alt+Drag is an OK temp solution, but this is starting to get really frustrating...

anybod find a fix?

---

### Post by crewe on 2008-02-21
I'm getting a dead link...

---

### Post by malachias on 2008-06-03
> **ashinshanghai said:**
> Forlong:

I am a total noobie to linux, and this was the simplest install I've done yet (and I love my new look). However, after getting Compiz Fusion up and running, I am now having problems with AmoraK and KTorrent. I keep getting pop-up messages (from both apps) that say:

"Cannot talk to klauncher"

I notice that the icon for Amorak that usually sits in the system tray upon minimization now just kind of hovers in space on the desktop. 

This is more annoying really than anything problematic, but it means I can't pull up Amorak on the current desktop, and I can't open torrent files directly from the current desktop either.


I don't know whether or not anyone's replied to this already since there's lots of pages after this, but I had a similar problem. The solution for me, whenever this happens, is to simply open up a konsole and run:
$ dcopserver_shutdown
$ kdeinit 
then restart the programs that won't dock (ktorrent, amarok, knetworkmanager, etc).

Hope that helps! And my apologies for an off-topic reply.

---

