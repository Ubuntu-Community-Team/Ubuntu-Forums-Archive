---
title: "Volume function keys on 12.04"
date: 2012-05-10
forum: Desktop Environments
---

### Post by billyseth on 2012-05-10
I installed 12.04, and was using it for while, then decided to explore some alternative desktops for it. 

I installed the Lubuntu packages, and am liking everything so far, except my keyboard volume keys aren't working. They were working under the normal gnome/unity desktop so I'm guessing that the DE handles the keyboard shortcuts.

My monitor brightness keys work as expected.

Any thoughts on what I should check out?

thanks!

---

### Post by zakhooi on 2012-07-27
> **billyseth said:**
> I installed 12.04, and was using it for while, then decided to explore some alternative desktops for it. 

I installed the Lubuntu packages, and am liking everything so far, except my keyboard volume keys aren't working. They were working under the normal gnome/unity desktop so I'm guessing that the DE handles the keyboard shortcuts.

My monitor brightness keys work as expected.

Any thoughts on what I should check out?

thanks!

I have exactly the same problems with Lubuntu 12.04 on a Eeepc 1015b.
Any suggestions?

---

### Post by Kevbo on 2012-10-18
Same here. Fresh install of Lubuntu 12.04 on Acer Aspire 725 and the Function Volume Keys don't work.  They worked with Ubuntu.  Any ideas, yet?  Anyone?  The computer is lightning fast with Lubuntu, so I would prefer Lubuntu to Unity.  But I do like my sound buttons.  :)

---

### Post by varunendra on 2012-10-19
Not precisely a help, but a similar experience I'd like to share-

@Kevbo,
I'm posting this from an Asus X54C laptop with default Ubuntu 12.04 with unity.
I intentionally disabled **asus_nb_wmi** driver (because it was causing problems with bluetooth which I needed more than these functions) on my laptop which has led it to the same behaviour. That is- 'Fn' key combinations for vol.control and touchpad enable/disable don't work anymore (they do as soon as I un-blacklist that module again, and reboot).

All other combinations (sleep, wifi enable/disable, brightness, vga-out) work perfectly (wifi-LED is dodgy though, but the wifi itself works perfectly regardless of the LED state). I should also mention that asus_wmi also stopped loading after blacklisting asus_nb_wmi.

Another similarity is that the blutooth was working fine with **Lubuntu** (which I had on an external USB HDD then), but I didn't check the modules or the 'Fn' key combinations on it.

So with that experience, I think you should check which modules are being loaded in both environments (Unity vs LXDE) with lsmod command:
```
lsmod
```
While it may be DE dependent, and the modules issue may be just a red herring, but it won't hurt checking. In your case, I guess it should be acer_wmi or a related driver that controls those keys.

As I write this, I'm getting more interested in the issue, and maybe I'll try Lubuntu again on a Live USB to see the difference, but only if time allows.

Also, take a look at "KeyTouch-editor" software (it's in the Software Center) which seems to address similar issues (but not sure as I've never tried it myself).

---

### Post by Kevbo on 2012-10-22
Thanks varunendra for the reply.  My lsmod for both unity and lxde are basically the same.  I'll take a look at keytouch-editor and keep playing around.

ETA: keytouch_editor doesn't work with lubuntu.

---

### Post by varunendra on 2012-10-25
> **Kevbo said:**
> keytouch_editor doesn't work with lubuntu.
Ouch! Time to see [LXDE forums]("http://forum.lxde.org/") I guess..
If you start a thread there, don't forget to put a link to this one as reference.

---

### Post by Herby Pepper on 2012-10-25
1.Open file:   leafpad ~/.config/openbox/lubuntu-rc.xml
fined "Keybinding for Volume management" section 

2.then copy that part of section that look like the one underneath and past it under but still in "Keybinding for Volume management" section.

 <keybind key="XF86AudioRaiseVolume">
      <action name="Execute">
          <command>amixer -q sset Master 3%+</command>
      </action>
    </keybind>

    <keybind key="XF86AudioLowerVolume">
      <action name="Execute">
          <command>amixer -q sset Master 3%-</command>
      </action>
    </keybind>

3.change keybind keys in copy text so it looks like that:
I made green the part which is changed.

  <!-- Keybinding for Volume management -->
    <keybind key="XF86AudioRaiseVolume">
      <action name="Execute">
          <command>amixer -q sset Master 3%+</command>
      </action>
    </keybind>

    <keybind key="XF86AudioLowerVolume">
      <action name="Execute">
          <command>amixer -q sset Master 3%-</command>
      </action>
    </keybind>

    <keybind key="[COLOR=YellowGreen]A-w[/COLOR]">
      <action name="Execute">
          <command>amixer -q sset Master 3%+</command>
      </action>
    </keybind>

    <keybind key="[COLOR=YellowGreen]A-f[/COLOR]">
      <action name="Execute">
          <command>amixer -q sset Master 3%-</command>
      </action>
    </keybind>


4.save file.

5.run in terminal:
openbox --reconfigure

Now pressing Alt+w sound should go up and Alt+f down. 
you can change keybind key the way it suits you. but remember some key or combination of keys have there function already, so choose them carefully. 



Another solution Keybinder program:

"keybinder is a graphical application for editing openbox keyboard shortcuts.  This phase of development, but it is usable and relatively stable."

[http://translate.googleusercontent.com/translate_c?depth=1&hl=en&ie=UTF8&prev=_t&rurl=translate.google.com&sl=auto&tl=en&twu=1&u=http://lambda.host22.com/%3Fpage%3Dkeybinder&usg=ALkJrhjZxOVTYISZxu5ouMKC1peaBlsg5Q](http://translate.googleusercontent.com/translate_c?depth=1&hl=en&ie=UTF8&prev=_t&rurl=translate.google.com&sl=auto&tl=en&twu=1&u=http://lambda.host22.com/%3Fpage%3Dkeybinder&usg=ALkJrhjZxOVTYISZxu5ouMKC1peaBlsg5Q)

---

### Post by Kevbo on 2012-10-25
It was a nice try, HP, but I still can't seem to get any configuration to work when I edit the lubuntu-rc.xml config file.  I am beginning to wonder if maybe there is something wrong in the execute command, maybe not connecting to alasamixer?  But I don't know how to check that.

Another oddity, the fn-Left and fn-Right work just fine to adjust the brightness, but I can't find their keybinding anywhere in the config file. I was hoping to maybe use them to engineer the fn-Up and fn-Down for the volume.  Keybinder is a nice little gui, but no help there, either.  Thanks for trying.  I'll gladly try any other ideas. :)

---

### Post by Kevbo on 2012-10-25
Wow! Don't know how I missed this one before, but it solved my function button problem.  Looks like it was a command issue.  Thanks to lun at Lubuntu Audio Issues at [http://ubuntuforums.org/showthread.php?t=1956323](http://ubuntuforums.org/showthread.php?t=1956323) from back in April. Oh well, every search doesn't find everything.

I added  "-D  pulse" ,  not the quotes, to the existing config file lubuntu-rc.xml like lun suggested, and even added it to the mute section and now the fn-F8 mute button works.:)  Everything is working!

    <keybind key="XF86AudioRaiseVolume">
      <action name="Execute">
        <command>amixer -q -D pulse sset Master 3%+ unmute</command>
      </action>
    </keybind>
    <keybind key="XF86AudioLowerVolume">
      <action name="Execute">
        <command>amixer -q -D pulse sset Master 3%- unmute</command>
      </action>
    </keybind>
    <keybind key="XF86AudioMute">
      <action name="Execute">
        <command>amixer -q -D pulse sset Master toggle</command>
      </action>
    </keybind>

Thanks everyone for all your suggestions and help.

Kevbo

---

### Post by ronniew on 2012-10-25
obkey still works you just have to alter one file after installation

obkey will allow you to edit and add all keyboard shortcuts.

Download obkey [here]("https://launchpad.net/~alex-p/+archive/notesalexp-precise/+build/3315194/+files/obkey_1.0%2Bgit20111228-2ppa1%7Eprecise1_all.deb"). and install it.

Then go to your run menu or in the terminal and paste the following

gksu leafpad /usr/bin/obkey

find the line 

/.config/openbox/rc.xml

change it to

/.config/openbox/lubuntu-rc.xml

save file and close

then launch obkey (usually in preferences menu)

and add or alter as many keys as you like

---

### Post by unheeding on 2012-11-03
> **Kevbo said:**
> Wow! Don't know how I missed this one before, but it solved my function button problem.  Looks like it was a command issue.  Thanks to lun at Lubuntu Audio Issues at [http://ubuntuforums.org/showthread.php?t=1956323](http://ubuntuforums.org/showthread.php?t=1956323) from back in April. Oh well, every search doesn't find everything.

I added  "-D  pulse" ,  not the quotes, to the existing config file lubuntu-rc.xml like lun suggested, and even added it to the mute section and now the fn-F8 mute button works.:)  Everything is working!

    <keybind key="XF86AudioRaiseVolume">
      <action name="Execute">
        <command>amixer -q -D pulse sset Master 3%+ unmute</command>
      </action>
    </keybind>
    <keybind key="XF86AudioLowerVolume">
      <action name="Execute">
        <command>amixer -q -D pulse sset Master 3%- unmute</command>
      </action>
    </keybind>
    <keybind key="XF86AudioMute">
      <action name="Execute">
        <command>amixer -q -D pulse sset Master toggle</command>
      </action>
    </keybind>

Thanks everyone for all your suggestions and help.

Kevbo


Thanks so much for this!  Worked for me too.  Cheers.

---

