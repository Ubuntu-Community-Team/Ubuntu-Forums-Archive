---
title: "Two panels?"
date: 2012-02-09
forum: Desktop Environments
---

### Post by sosaudio1 on 2012-02-09
Ok so I am using Unity and have my panel bar's opacity turned down using CCSM. Recently I clicked on "Main Menu" to add an application launcher. It worked. I have added the application launcher to applications so that I can just click it instead of cli everytime...but now I have a different problem.

Looks like I have a secondary panel bar under the unity bar possibly main menu. Under the opacity with blur, it looks like I can make out history, tools, help......

I noticed in gnome-shell, if you tell the panel to auto-hide, it does, revealing a secondary panel with the usual options. Is there a way to get rid of the secondary panel and just stick with unity's panel?

I can get rid of it in CCSM by turning opacity all the way off....but this then makes it clear and I want some shade in the bar.

Any help would be awesome thanks

Rich

***Thread has been solved. Workaround on last page.* I will continue to monitor the system and if it errors out again I will bump the thread. Dev's, this is a workaround there are issues with it. Not major, they affect polish of the Desktop experience**

**Part TWO: so as you will read at the end of this thread, Unity Launcher dodging is working correctly now....this after doing some updates. Can't tell if the two are related or not...my first inclination is to say, it did not...but you can shed more light on this..so bottom line, top panel is fixed with workaround and dodging of the launcher appears good**

---

### Post by sosaudio1 on 2012-02-10
> **sosaudio1 said:**
> Ok so I am using Unity and have my panel bar's opacity turned down using CCSM. Recently I clicked on "Main Menu" to add an application launcher. It worked. I have added the application launcher to applications so that I can just click it instead of cli everytime...but now I have a different problem.

Looks like I have a secondary panel bar under the unity bar possibly main menu. Under the opacity with blur, it looks like I can make out history, tools, help......

I noticed in gnome-shell, if you tell the panel to auto-hide, it does, revealing a secondary panel with the usual options. Is there a way to get rid of the secondary panel and just stick with unity's panel?

I can get rid of it in CCSM by turning opacity all the way off....but this then makes it clear and I want some shade in the bar.

Any help would be awesome thanks

Rich

Anyone know why this is happening? Side note 1: I noticed it fixes if, in CSSM, I click something like Desktop Magnifier or turn off Magnifier. But when I reboot, it is bad again

Rich

---

### Post by Frogs Hair on 2012-02-10
This happened to me after an update once  and I used the opacity slider work around as you did . It has not happened since and , so the cause is unknown in my case . I run the Gnome Shell as well as Unity and it appeared as though the gnome panel was running under the unity panel . That makes me think it had something to with the gnome-settings-daemon  .

---

### Post by sosaudio1 on 2012-02-10
> **Frogs Hair said:**
> This happened to me after an update once  and I used the opacity slider work around as you did . It has not happened since and , so the cause is unknown in my case . I run the Gnome Shell as well as Unity and it appeared as though the gnome panel was running under the unity panel . That makes me think it had something to with the gnome-settings-daemon  . I can 

Yeah...there has got to be a way to remove that panel and just have the unity panel. I know I can kill it by playing with settings inside of cssm. So there has got to be a workaround. Is there a command to kill just the panel? Or a place to comment out?

This has got to be easy
Rich

---

### Post by sosaudio1 on 2012-02-11
> **sosaudio1 said:**
> I can 

Yeah...there has got to be a way to remove that panel and just have the unity panel. I know I can kill it by playing with settings inside of cssm. So there has got to be a workaround. Is there a command to kill just the panel? Or a place to comment out?

This has got to be easy
Rich

Here is another way I have found that gits rid of that panel...if for a bit.....in cssm and the unity plugin, if you mess with the opacity of the top panel, going all the way to the right and then backing off, it will begin clear out the second panel and the opacity can be set correctly....

Now to reboot and see if those settings fixed it.

---

### Post by sosaudio1 on 2012-02-11
> **sosaudio1 said:**
> Here is another way I have found that gits rid of that panel...if for a bit.....in cssm and the unity plugin, if you mess with the opacity of the top panel, going all the way to the right and then backing off, it will begin clear out the second panel and the opacity can be set correctly....

Now to reboot and see if those settings fixed it.

Ahem CCSM!!! 

Ok so after a reboot the panel was indeed back under the unity panel. Playing around again in CCSM made it reset the unity panel minus the second panel.

What if I made an autostart that killed the gnome-panel. Would that work?

The thought is, it starts then starts to draw the desktop, the auto start command then kills gnome-panel and the unity panel remains...it would be a workaround until we get it fixed....



Anybody anybody???

---

### Post by bogan on 2012-02-11
Hi!, **sosaudio1**.
Have you checked if Unity 2d launcher is active, and what do you get if you log in to GnomeClassic?
```
ps ax | grep unity
``` will tell you what is running.

I had a situation similar to what you describe but the Unity Panel was on auto hide, the 2d Panel was not.
The MyUnity program allowed me to reduce the width of one but not the other, so that both were accessible.

The Unity Panel was the default set-up, the other  was one I had created myself and Alt+Right-Click on it gave the options to create, move, remove or change Properties, whereas on the Unity Panel Alt+Right-Click had no effect.

I do not know if this has anything to do with your issue but thought it might help.

Chao!, **bogan.**

---

### Post by sosaudio1 on 2012-02-11
> **bogan said:**
> Hi!, **sosaudio1**.
Have you checked if Unity 2d launcher is active, and what do you get if you log in to GnomeClassic?
```
ps ax | grep unity
``` will tell you what is running.

I had a situation similar to what you describe but the Unity Panel was on auto hide, the 2d Panel was not.
The MyUnity program allowed me to reduce the width of one but not the other, so that both were accessible.

The Unity Panel was the default set-up, the other  was one I had created myself and Alt+Right-Click on it gave the options to create, move, remove or change Properties, whereas on the Unity Panel Alt+Right-Click had no effect.

I do not know if this has anything to do with your issue but thought it might help.

Chao!, **bogan.**

Thanks Bogan!

```
$ ps ax | grep unity
 1826 ?        S      0:02 /usr/bin/unity-window-decorator
 1887 ?        Sl     0:01 /usr/lib/unity-lens-applications/unity-applications-daemon
 1889 ?        Sl     0:00 /usr/lib/unity-lens-files/unity-files-daemon
 1891 ?        Sl     0:00 /usr/lib/unity-lens-music/unity-music-daemon
 1930 ?        Sl     0:00 /usr/lib/unity-lens-music/unity-musicstore-daemon
 2165 ?        Sl     0:06 /usr/lib/unity/unity-panel-service
 2680 pts/0    S+     0:00 grep --color=auto unity
```

This is what is running now....Lemmie reboot and will do the same command and see what we have running after


Rich

---

### Post by sosaudio1 on 2012-02-11
> **sosaudio1 said:**
> Thanks Bogan!

```
$ ps ax | grep unity
 1826 ?        S      0:02 /usr/bin/unity-window-decorator
 1887 ?        Sl     0:01 /usr/lib/unity-lens-applications/unity-applications-daemon
 1889 ?        Sl     0:00 /usr/lib/unity-lens-files/unity-files-daemon
 1891 ?        Sl     0:00 /usr/lib/unity-lens-music/unity-music-daemon
 1930 ?        Sl     0:00 /usr/lib/unity-lens-music/unity-musicstore-daemon
 2165 ?        Sl     0:06 /usr/lib/unity/unity-panel-service
 2680 pts/0    S+     0:00 grep --color=auto unity
```

This is what is running now....Lemmie reboot and will do the same command and see what we have running after


Rich

Same problem upon reboot. I removed the Unity 2d panel to see if that made a difference. No change

I booted in Gnome 2d and removed the top panel...no change either...

The same issue remains, secondary panel under the Unity panel


Gonna try to swap to Gnome shell and see if I can remove that panel there and see what comes of it

Rich

---

### Post by sosaudio1 on 2012-02-12
> **sosaudio1 said:**
> Same problem upon reboot. I removed the Unity 2d panel to see if that made a difference. No change

I booted in Gnome 2d and removed the top panel...no change either...

The same issue remains, secondary panel under the Unity panel


Gonna try to swap to Gnome shell and see if I can remove that panel there and see what comes of it

Rich

Tried to figure that out and could not. CTRL+Right Click didn't offer up results.

Still think this has got to be an easy fix...just not sure where to go

---

### Post by bogan on 2012-02-13
Hi!. **sosaudio1**.

You Posted:>  Tried to figure that out and could not.[COLOR=Green]**[COLOR=Red]CTRL+Right Click[/COLOR] **[/COLOR]didn't offer up results. Still think this has got to be an easy fix...just not sure where to go It should be:[COLOR=Blue] Alt+Right-Click[/COLOR] to give the options to create, move, remove or change  Properties,  or: Super [Win]+Right-Click, or even:  Super [Win]+Alt+Right-Click , not [COLOR=Red]Ctrl+Right-Click[/COLOR].

Chao!, **bogan**.

---

### Post by sosaudio1 on 2012-02-13
> **bogan said:**
> Hi!. **sosaudio1**.

You Posted: It should be:[COLOR=Blue] Alt+Right-Click[/COLOR] to give the options to create, move, remove or change  Properties,  or: Super [Win]+Right-Click, or even:  Super [Win]+Alt+Right-Click , not [COLOR=Red]Ctrl+Right-Click[/COLOR].

Chao!, **bogan**.

Yeah...Forgot about SUPER...I will try that when I get home. If in Gnome Classic, I remove that panel, should it disappear when in Unity?

Think what I might do is go to all the log-ins and remove the top panel. Here is the weird part. In one of the environments, I removed the top panel and created a bottom panel. If this is truly an issue, shouldn't the bottom panel show up in Unity?

Why would these transfer to different environments?

Thanks for your help
Rich

---

### Post by Frogs Hair on 2012-02-13
Hello ,

This problem occurred again , so I started looking for a running process . various kill panel commands didn't work . While logged into the Gnome Shell I checked looking glass , which is an error reporting and trouble shooting tool .

I discovered a nautilus error and ran the nautilus restart command , which will work in Unity also .```
nautilus -q
``` 

The mystery panel disappeared . It's not a Gnome or Unity panel running under the other panel it is caused by nautilus . This is only a work around , but it may help until a fix is found .

---

### Post by Frogs Hair on 2012-02-13
I located another work around . Open Advanced Settings and under Desktop disable "have file manager handle the desktop."

---

### Post by Krytarik on 2012-02-13
> **Frogs Hair said:**
> It's not a Gnome or Unity panel running under the other panel it is caused by nautilus .
> **Frogs Hair said:**
> Open Advanced Settings and under Desktop disable "have file manager handle the desktop."
I was following this thread right from the start, and I guess you are right about that, but you know what's weird? The OP stated this right then:
> **sosaudio1 said:**
> Looks like I have a secondary panel bar under  the unity bar possibly main menu. Under the opacity with blur, it looks  like I can make out **history, tools, help......**
And there are no "History" and "Tools" menu items in Nautilus; maybe the OP wasn't that exact then, and simply stated those from Firefox instead!?

---

### Post by sosaudio1 on 2012-02-13
> **Krytarik said:**
> I was following this thread right from the start, and I guess you are right about that, but you know what's weird? The OP stated this right then:

And there are no "History" and "Tools" menu items in Nautilus; maybe the OP wasn't that exact then, and stated those from Firefox instead!?

Glad to know you were following from start. I am not sure what they were...are...due to the fact that the unity bar using opacity also adds blur. If I try and make the unity bar...clear...it makes the bar below clear as well. Soooo not sure what the menu options are they gave the same size and shape as file edit history bookmarks etc. It is not the Firefox menu because firefox is not running all the time and that bar is there regardless of what is running....Frog...I think you are on to it. Here is why I say that. 

When I get rid of that setting, it looks like drop shadow on the unity bar dissappears. Now, given the color of the offending bar, it stands to reason that the blur effect on the unity bar is causing artifacts that appear to be drop shadow when infact, it is just blur acting out on the bar below.

Sooo I will remove the control there of File manager messing with Desktop and see what results I get....first tho...dinner.


Rich

---

### Post by sosaudio1 on 2012-02-13
> **sosaudio1 said:**
> Glad to know you were following from start. I am not sure what they were...are...due to the fact that the unity bar using opacity also adds blur. If I try and make the unity bar...clear...it makes the bar below clear as well. Soooo not sure what the menu options are they gave the same size and shape as file edit history bookmarks etc. It is not the Firefox menu because firefox is not running all the time and that bar is there regardless of what is running....Frog...I think you are on to it. Here is why I say that. 

When I get rid of that setting, it looks like drop shadow on the unity bar dissappears. Now, given the color of the offending bar, it stands to reason that the blur effect on the unity bar is causing artifacts that appear to be drop shadow when infact, it is just blur acting out on the bar below.

Sooo I will remove the control there of File manager messing with Desktop and see what results I get....first tho...dinner.


Rich

SUCCESS!!!! I will mark this as solved!!! 

Ok so the advanced settings "let file manager handle the desktop" is where the issue was.

Once removing that option in the Advanced Settings, it got rid of the extra panel...however..now the launcher bar doesn't "dodge" like it used to. It does dodge...the windows have to be in restore not maximized mode.

Dev's here is one for you to note...

My recommendations would be, in advanced settings "Let File Manager Control Desktop" option, I would either kill the Unity Panel or add the option for Unity Panel to autohide. IF the option to "Let File Manager Control Desktop" is unticked, then Dodge should work as before with the cursor capable of accessing the Launcher.

My .02 cents


Rich

---

### Post by Frogs Hair on 2012-02-13
What I saw today and the first time was the nautilus panel that appears if Unity crashes . It gives access to places but not to an applications menu . I was able to remove its appearance by moving opacity slider but I am pretty sure it was still running . Restarting nautilus seems to stop the process. 

The second work around regarding Advanced Settings I found at Ask Ubuntu . This is not practical because of the inability to use the desktop to move files .

---

### Post by sosaudio1 on 2012-02-13
> **Frogs Hair said:**
> What I saw today and the first time was the nautilus panel that appears if Unity crashes . It gives access to places but not to an applications menu . I was able to remove its appearance by moving opacity slider but I am pretty sure it was still running . Restarting nautilus seems to stop the process. 

The second work around regarding Advanced Settings I found at Ask Ubuntu . This is not practical because of the inability to use the desktop to move files .

True this is why it is a work around. If we didn't have this option I was going to try the nautilus -q that you posted and if that worked I was going to make an autostart option that would kick that at boot time. But again, that is a work around and as you said...not practical as I am sure that would only mask any deeper issues that nautilus would be trying to tell us.

No to the next story....DEVS....the panel dodge works as it should...did some upgrades just a second ago and now it is working...can't say if the two are related but hey, it works now.

---

