---
title: "How to disable touchpad tapping ?"
date: 2011-06-14
forum: Desktop Environments
---

### Post by GoGoThomas on 2011-06-14
Hello Ubuntu gurus,

I'm a beginner with Ubuntu and very recently installed Ubuntu 9.0.4 on an Acer 8943G laptop.

The first thing I usually do when I install an OS on a laptop is to  disable the touchpad tapping (or tap-to-click or whatever you want to  call it). On this machine I have installed a triple boot  WinXP-Win7-Ubuntu9.0.4 and I was able to disable the touchpad tapping  without problem on WinXP and Win7.

I would like to try and explore Ubuntu but after 3 days of investigation  I still haven't been able to disable the touchpad tapping on Ubuntu.

I tried the various tricks found in forums like shmconfig.fdi, xorg.conf, synclient, modprobe psmouse, i8042.nopnp, etc...

The best I could achieve is to make the Touchpad tab appears in the  mouse preference, but checking/unchecking the options didn't have any  effect.
Also I was able to completely turn off or on the touchpad using synclient touchpadoff.
I was also able at some point to disable tapping but it also disabled the touchpad buttons so not useful.

Basically the only thing I want is the touchpad to work as basically as  possible ie being able to simply move the cursor and clicking using the  touchpad buttons. I don't want all the tapping / scrolling and who knows  what, all that stuff drives me nuts.

As I did a lot of experiments my setup started to get a bit dirty so now  I have completely reinstall Ubuntu from scratch and so my config is  absolutely untouched.

Would a generous soul help me trying to disable the touchpad tapping by  suggesting me to try some stuff (the only things I don't want to do is  stuff like installing a new Linux version or upgrading/recompiling the  kernel etc...). You can ask me whatever you want in terms of providing  you with config file and log file content, etc... As I can't properly  use Ubuntu with the touchpad tapping on, basically you are my only  chance of being able to carry on exploring Ubuntu, many thanks in  advance folks and I hope you'll be able to help me and convert me into a  happy Ubuntu user.

---

### Post by Joe of loath on 2011-06-14
First off, uninstall 9.04 and install a supported version like 10.04 or 11.04. You will run into problems using 9.04 (As you are), and security updates stopped ages ago. It may even fix your current issues!

---

### Post by GoGoThomas on 2011-06-14
Thanks for the suggestion but as mentioned I don't want to do stuff like upgrading to a new OS version.
WinXP is 10 years old and I was able to disable the touchpad tapping without problems.
Ubuntu 9.04 is only 2 years old so I guess this is feasible.

---

### Post by Joe of loath on 2011-06-14
Using Ubuntu 9.04 is the equivilant of using Windows 98. It's unsupported. You just reinstalled, what's the problem with doing it again? 10.04 is supported for another 2 years, it's the most stable of all the currently supported Ubuntu releases, and you don't have to deal with convoluted fixes to install simple things like Firefox 4 ;)

---

### Post by Copper Bezel on 2011-06-14
Apples to guavas - first, XP SP3 most certainly isn't ten years old, and second, Ubuntu's release cycle and Windows' don't resemble. 

The particular problem you're trying to solve doesn't have anything to do with the version, but you really shouldn't have "recently installed" a two-year-old non-LTS Ubuntu edition. You might need some additional software, and not having access to supported repositories makes your system essentially useless. 

If there's a specific problem that's keeping you from updating to 10.04 (which has two years of support left) then it would be more sensible to solve *that* problem. The fact that your tap-to-click setting isn't getting set could be due to a couple of different factors, and it could be a bug that's been fixed. If it's using the Synaptics drivers, you could also try setting this directly through synclient, but it's messy to get *that* to stick.

---

### Post by GoGoThomas on 2011-06-14
Thank you for your suggestions but I live in the country side and I have a slow connection (I plug my smartphone into my computer to access the Internet) so that would take me ages to upgrade to a new version. It sounds crazy to me to have to upgrade to a new OS version just to be able to disable the touchpad tapping, there must be a way.
For example is there a way to make Ubuntu see the touchpad as if it was a mouse ie only cursor movement and button clicks ? I am not asking for more functionality, I am asking for less so there must be a way. If someone could provide me some leads so that I can try many thanks in advance.

---

### Post by Copper Bezel on 2011-06-14
Well, if you're using the Synaptics driver, you should be able to run 

```
synclient MaxTapTime=0
```

for the present session, then set it as a Startup Application so it'll be set each time you log in.

---

### Post by Joe of loath on 2011-06-14
> **GoGoThomas said:**
> Thank you for your suggestions but I live in the country side and I have a slow connection (I plug my smartphone into my computer to access the Internet) so that would take me ages to upgrade to a new version. It sounds crazy to me to have to upgrade to a new OS version just to be able to disable the touchpad tapping, there must be a way.
For example is there a way to make Ubuntu see the touchpad as if it was a mouse ie only cursor movement and button clicks ? I am not asking for more functionality, I am asking for less so there must be a way. If someone could provide me some leads so that I can try many thanks in advance.

Ask a friend with a fast internet connection to burn you off a copy of 10.04 :D

---

### Post by GoGoThomas on 2011-06-14
Joe : thanks for the idea but I don't have that many friends, they live  in the country side as well and I am the pioneer with Ubuntu amongst  them :-) But if I find a way to get the touchpad tapping off, I'll try  to convert a few of them :-)

Copper :
When I enter
synclient MaxTapTime=0
I get:
Can't access shared memory area. SHMConfig disabled?

I've been able to turn SHMConfig on before reinstalling Linux but I  would like you (or someone else who knows) to tell me exactly how you  would do that because I don't want to introduce new problems if I do it  by myself. So could you explain me precisely the best procedure to  enable SHM ?

---

### Post by Copper Bezel on 2011-06-14
I really couldn't, because I never had to do that, even though my first Synaptics trackpad was under 9.04. Odd. Does the file referred to in [this guide]("http://www.samlesher.com/code/enable-shmconfig-for-synaptics-touchpad-on-ubuntu-intrepid-ibex-810\") exist for you? It's not used in the current version.

---

### Post by GoGoThomas on 2011-06-14
Copper, yes this file exists indeed :

cat /usr/share/hal/fdi/policy/20thirdparty/11-x11-synaptics.fdi
<?xml version="1.0" encoding="ISO-8859-1"?>
<deviceinfo version="0.2">
  <device>
    <match key="info.capabilities" contains="input.touchpad">
        <merge key="input.x11_driver" type="string">synaptics</merge>
        <!-- Arbitrary options can be passed to the driver using
             the input.x11_options property since xorg-server-1.5. -->
        <!-- EXAMPLE:
        <merge key="input.x11_options.LeftEdge" type="string">120</merge>
        -->
    </match>
  </device>
</deviceinfo>

But the content looks different from the one mention in the article (there is no "info.product" section).
What do you think I should do ?

---

### Post by Copper Bezel on 2011-06-14
It looks like it would come after the -->, there. Worth a shot - I don't know beyond that. Otherwise, you might just have to live with it until you can get the system upgraded.

---

### Post by GoGoThomas on 2011-06-14
So as you suggested I've added the line:

<merge key="input.x11_options.SHMConfig" type="string">On</merge>

in the file /usr/share/hal/fdi/policy/20thirdparty/11-x11-synaptics.fdi

and now this file looks like that :

<?xml version="1.0" encoding="ISO-8859-1"?>
<deviceinfo version="0.2">
  <device>
    <match key="info.capabilities" contains="input.touchpad">
        <merge key="input.x11_driver" type="string">synaptics</merge>
        <!-- Arbitrary options can be passed to the driver using
             the input.x11_options property since xorg-server-1.5. -->
        <!-- EXAMPLE:
        <merge key="input.x11_options.LeftEdge" type="string">120</merge>
        -->
        <merge key="input.x11_options.SHMConfig" type="string">On</merge>
    </match>
  </device>
</deviceinfo>

I've rebooted and executed
synclient MaxTapTime=0
but I still get the answer
Can't access shared memory area. SHMConfig disabled?

So it doesn't look it had any effect.

Thanks copper for your help very appreciated, at least it's a start.

Would someone else be able to take me further ?!

---

### Post by GoGoThomas on 2011-06-15
You the present reader of this message, would you have any ideas, suggestions or pointers to help me enable SHM ?! Many thanks in advance :-)

---

### Post by GoGoThomas on 2011-06-16
My problem was solved and I am now able to enable/disable tap-to-click at will.

The problem was solved by upgrading the kernel to version 2.6.38 (I did not have to do a full Ubuntu upgrade)
After rebooting I had a "Touchpad" tab in Mouse Preferences (I don't have this tab by default when I boot with kernel 2.6.28 ). Unchecking "Enable mouse clicks with touchpad" works and disables touchpad tapping (even if I was able to make this option appear under kernel 2.6.28, unchecking the option did not have any effect)

For more background information, specially on updating the kernel, check that thread:
[http://ubuntuforums.org/showthread.php?t=1783265](http://ubuntuforums.org/showthread.php?t=1783265)

Thank you.

---

### Post by Copper Bezel on 2011-06-16
Very cool! I'm glad you got this worked out. = )

---

### Post by GoGoThomas on 2011-06-16
Thank you very glad too and thanks for your help :D

---

### Post by dhinteractive on 2011-06-16
many thanks in  advance folks
many thanks in  advance folks

---

