---
title: "ICEWM: How to disable keyboard shortcuts?"
date: 2014-05-21
forum: Desktop Environments
---

### Post by abcuser on 2014-05-21
Hi,
I have installed "Ubuntu 14.04 Server minimal install" and installed ICEWM as desktop environment. I have installed VirtualBox virtualization program and inside Windows 7 as virtual guest.

Now in Ubuntu (ICEWM) when I click for example on Super+d it minimizes applications in ICEWM desktop environment. So far no problem.

Now I start a Windows 7 as virtual guest and I would like to have Super+d to minimize windows in Windows 7, but this keyboard shortcut is accepted by ICEWM and not by Windows 7. I see a lot of keyboard shortcuts do not work in Windows 7, but instead are accepted by ICEWM desktop environment.

**QUESTION:** How to turn ICEWM keyboard shortcuts off and let Windows 7 virtual guest to accept those keyboard shortcuts?

So far according to reading documentation I did:
1. Create directory for ICEWM user specific settings:
```
cd ~
mkdir .icewm
cd .icewm

```
2. Created a keys file and opened it with vim editor:
```
vim keys
```
3. General syntax for keys is:
key "some_keyboard_shortcut_combination" program_to_execute
Sample: key "Super+d" xterm
The above command would launch a terminal.

So in my case I did:
```
key "Super+d"
```
and left program_to_execute parameter empty.
4. I restarted ICEWM by executing CTRL+ALT+DEL and clicked on "Restart icewm" button.
5. Checking the keyboard shortcut Super+d and has no effect, which is what is expected because of code in step 3.
6. Starting Windows 7 and keyboard shortcut Super+d is no longer accepted by ICEWM, but on other case it is also not accepted by Windows 7. When keyboard shortcut is pressed nothing happens. I would like that Windows 7 is accepting Super+d keyboard combination and minimizes all of the windows on desktop.

It looks to me that above steps are not a proper way to disable ICEWM keyboard shortcut. I just can't find anything on web how to properly disable keyboard shortcut in ICEWM.

Any help is greatly appreciated.

P.S. The best documentation I have manage to find of web is:
[http://www.icewm.org/FAQ/IceWM-FAQ-4.html](http://www.icewm.org/FAQ/IceWM-FAQ-4.html)
[http://crunchbang.org/forums/viewtopic.php?id=12940](http://crunchbang.org/forums/viewtopic.php?id=12940)
Thanks

---

