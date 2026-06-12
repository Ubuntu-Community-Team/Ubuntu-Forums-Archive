---
title: "Thunderbird instead of Evolution. How?"
date: 2011-03-29
forum: Desktop Environments
---

### Post by rez182 on 2011-03-29
i want to place the thunderbird mail in the place of evolution mail and remove evolution. how do i do it?

---

### Post by vanadium on 2011-03-29
Install Evolution using the Software Center.

In an Ubuntu install, you cannot completely remove evolution. So better leave it alone: it will not be in the way.

---

### Post by deconstrained on 2011-03-29
Something I recommend for using Thunderbird: the [Evolution Mirror](https://addons.mozilla.org/en-US/thunderbird/addon/evolution-mirror/) plugin for Thunderbird. Works like a charm.

---

### Post by SeijiSensei on 2011-03-29
In answer to your question, just install thunderbird from the repositories.  Transferring your messages from Evolution to Thunderbird is more of the issue.  I suggest reading some online documentation about importing Evolution folders to Thunderbird.  Whether you use IMAP or POP is another important issue.  If you're using IMAP with Evolution, and all your folders reside on the server, making the transition to Thunderbird should be pretty painless.

---

### Post by rez182 on 2011-03-29
[SeijiSensei]("http://ubuntuforums.org/member.php?u=698195")

i dont need to do them because im new to ubuntu and i did not do much with evolution mail. i just want thunderbird in that place instead of evolution. (thunderbird acting like the default mailing system and the ability to click and get mails right from the top panel)

also empathy messenger seems to not work with hotmail... any suggestion to a good chat client?

thanks everyone...

---

### Post by Krytarik on 2011-03-29
> **rez182 said:**
> 
i dont need to do them because im new to ubuntu and i did not do much with evolution mail. i just want thunderbird in that place instead of evolution. (thunderbird acting like the default mailing system and the ability to click and get mails right from the top panel)
 
1.) Removal of Evolution:

purge all packages found with "evolution", except of those:
- evolution-data-server-common
- evolution-data-server (needed for "About Me")

2.) Integrate Thunderbird into the "indicator-message" applet (the envelope at the panel):

a) create the file "/usr/share/indicators/messages/applications/thunderbird", with those content:
```
/usr/share/applications/thunderbird.desktop
```b) install Thunderbird Indicator
[https://launchpad.net/~ruben-verweij/+archive/thunderbird-indicator]("https://launchpad.net/%7Eruben-verweij/+archive/thunderbird-indicator")
```
sudo add-apt-repository ppa:ruben-verweij/thunderbird-indicator
sudo apt-get update
sudo apt-get install xul-ext-indicator 

```> **rez182 said:**
> 
also empathy messenger seems to not work with hotmail... any suggestion to a good chat client?

a) Pidgin: I use it with ICQ and MSN, however it doesn't support the special features of MSN.

b) Emesene: based on QT, supports most of the special features of MSN.

---

### Post by rez182 on 2011-03-31
@[Krytarik]("http://ubuntuforums.org/member.php?u=1187548")

i never used codes in the terminal before, and i kinda don know how this works. do i "just" have to input these codes in the terminal? and everything will happen autometically?

Pidgin got me a little worried when i read the information in Ubuntu software centre. there was a plugin called pidgin off the record plugin, which said it gives the ability to keep the conversation secured from others to be able to read it. :O thats scary. then everything in linux seems to be connected to privacy matters in someway. could linux be risky for in-experianced users? is linux safer in privacy matters compared to windows? sorry for the off-tipic question.

thanks for your time n support [Krytarik]("http://ubuntuforums.org/member.php?u=1187548") and everyone else...

---

### Post by vanadium on 2011-03-31
With respect to the terminal commands: open a terminal (Applications - Accessories - terminal) and copy paste each command one by one to execute them. The first time you paste a command starting with "sudo", you will be asked for your login password.

And yes, these few commands will perform installation and configuration automatically.

---

### Post by Krytarik on 2011-03-31
> **rez182 said:**
> 
i never used codes in the terminal before, and i kinda don know how this works. do i "just" have to input these codes in the terminal? and everything will happen autometically?
Regarding (1), you may use Synaptic to search for the relevant packages and remove/purge them.

If you choose to use Thunderbird Indicator, you need only to run the commands stated under (2 b), and yeah, just like *vanadium* said, simply copy & paste & enter. Then relogin to make it affect the indicator. You will find its options in Thunderbird's add-on management.

And I do really recommend it, I've just upgraded it right after writing the previous post, and it's better than ever. Before I had a version of it offered on Mozilla's add-on site, and had some issues with those just recently. But those issues are fixed in the new version, and it even includes a previously missing option. I just came across the PPA (again), after I noticed that it isn't available anymore at Mozilla Add-ons, when I checked its bookmark for your thread.
> **rez182 said:**
> 
Pidgin got me a little worried when i read the information in Ubuntu software centre. there was a plugin called pidgin off the record plugin, which said it gives the ability to keep the conversation secured from others to be able to read it. :O thats scary.
You need to know, that *any* conversion via instant messaging networks is per-se unencrypted/unsecure, like it's also the case with emails! So, providing a plugin to secure those is actually worth a bonus point.
> **rez182 said:**
> 
then everything in linux seems to be connected to privacy matters in someway. could linux be risky for in-experianced users? is linux safer in privacy matters compared to windows? sorry for the off-tipic question.
Yeah, Linux is much safer than Windows! You really don't need to care about any kind of malware.

---

### Post by rez182 on 2011-04-02
the update manager was installing updates in the background when i input the first 3 codes out of the 4. then something happened and i needed to restart, after restart the boot manager where i choose which boot to load (eg ubuntu, ubuntu recovery, memory test x2, win7) it changed to:

ubuntu 2.x.x.x
ubuntu 2.x.x.x recovery
ubuntu 2.x.x.x.....................(repeat)
ubuntu 2.x.x.x recovery..... (repeat)
memory test........................(same)
memory test (something)....(same)
Win7.....................................(same)

any idea whats going on?

btw thanks for the help...im using thunder bird now..... :)

----------------------------------------------------------------------------------------------------------------------
i wanna ask an off topic question about pidgin. (thought no reason to open a thread for this)
are all messengers built in a way that there is no security? and only pidgin supports OTR? wat about windows live messenger, are they insecure too? or only the messengers in linux?

---

### Post by Krytarik on 2011-04-02
Actually, both questions are unrelated to the original topic. ;-)

The easier part first: Yeah, like I said, ALL messengers are per default insecure. But for some of them you may find plugins to secure the conversations.

As for the boot options, everytime when a kernel upgrade gets installed, the new kernel turns up at the boot menu, with both options, and since the options are getting added at the start, the normal boot option of the new will be selected by default.

But the old kernels will not get removed automatically, you have to do it on your own, but you should always retain at least the two most recent kernels. See here on how to remove the old kernel packages:
[http://ubuntuforums.org/showthread.php?t=1587462](http://ubuntuforums.org/showthread.php?t=1587462)

And you should definitely not only remove the kernel's image package, but also it's header packages, like described, since it frees up a lot of disk space! I recommend using Ubuntu Tweak for all that.

Also, are you really sure that the kernel version numbers at the boot menu are all the same!? I don't guess so.

Greetings.

---

### Post by rez182 on 2011-04-02
thanks alot it was a useful information.

---

### Post by rez182 on 2011-04-02
i cant install ubuntu tweak with that sudo code...

---

### Post by Krytarik on 2011-04-02
The guide describes the way to download the deb-package and install it manually.

But, actually, the better way is to add their PPA and install it through a package manager:
```
sudo add-apt-repository ppa:tualatrix/ppa
sudo apt-get update
sudo apt-get install ubuntu-tweak
```
You will find Ubuntu Tweak in "Applications -> System Tools" after the installation.

Sorry, I didn't check that guide to that aspect.

---

