---
title: "Stuck at login screen Loop, not even guest session works"
date: 2012-03-03
forum: Desktop Environments
---

### Post by mattsony on 2012-03-03
i restarted my computer after attempting to fix a bug with panel transparency and i put in a command i found here :[http://techhamlet.com/2012/03/an-ugly-menu-in-ubuntu-desktop/](http://techhamlet.com/2012/03/an-ugly-menu-in-ubuntu-desktop/)
When that didn't work i quit nautilus which still didn't work so then i just restarted my computer. When i turned it on, i was greeted with the login screen. I put in my password and pressed enter. the screen went black like it was logging in then it looped back into the login screen. i tried the guest session and it did the same thing. I tried random passwords and it just tells me it's the wrong password. Is there something I'm missing that is causing this? I'm a bit of  newb and I wanted to check out 12.04 and it ran awesome on this 7 year old computer but now this happened which is extremely annoying.

---

### Post by 23dornot23d on 2012-03-03
Will get some information first .... can you post back the results of this .....

Find out what Graphics you are running , cut and paste into a terminal window please

[B]lspci -v | perl -ne '/VGA/../^$/ and /VGA|Kern/ and print'


[/B]can you do Ctrl + Alt + F2 

and login to a console ?

will post the command here that you used .... as some people do not like clicking on links ....

```

echo '[ ${DESKTOP_SESSION#ubuntu} = $DESKTOP_SESSION ] &amp;&amp; unset UBUNTU_MENUPROXY' | sudo tee /etc/X11/Xsession.d/81ubuntu-menu-proxy



```

---

### Post by mattsony on 2012-03-03
I think it may have been because i used the command in unity. I thought it was the problem i was having when it obviously was not.

---

### Post by 23dornot23d on 2012-03-03
I will try to explain what I think that command does .....

after looking at what [[COLOR=Blue]**tee**[/COLOR]]("http://linux.101hacks.com/unix/tee-command-examples/") does .... which simply seems to write the preceding - to the screen and to a file

so 

${DESKTOP_SESSION#ubuntu} = $DESKTOP_SESSION && unset UBUNTU_MENUPROXY'

gets written to this file ......

/etc/X11/Xsession.d/[COLOR=Red]**81ubuntu-menu-proxy**[/COLOR]

So maybe someone can say what it does ...... as I do not use UNITY - *(am in KDE) ..... and that file does not seem to exist on my system .......

Hopefully this gives the thread a BUMP as such .... someone else may shed more light on whether that
file is needed ...... or not ......

---

### Post by Krytarik on 2012-03-03
Ok, let's clear this up now - hopefully *markbl* comes across this thread later, to notice that that blogger has inadvertently disfigured* the command he has [provided earlier]("http://ubuntuforums.org/showthread.php?p=11731452#post11731452"), and clear it up on that end, but let's not wait for that. ;-)

* he converted the "&&" into the HTML entities "&amp;&amp;" - that's the cause of interrupting the start of *any* X session

So, to fix this, you just need to remove the previously created file via the console/tty:

[LIST=1]
[*]At the login screen, press Ctrl+Alt+F1 to switch to tty1.
[*]Log in there.
[*]Remove that file to revert to the default:
```
sudo rm /etc/X11/Xsession.d/81ubuntu-menu-proxy
```
[*]Press Ctrl+Alt+F7 to switch back to the login screen.
[/LIST]
Try again to log in; should work now.

Reg. your original plan, that command would disable Global Menu in any *non*-Unity sessions; so it wouldn't have helped you anyway. ;-) And I believe you don't really want to disable Global Menu in Unity :P ; but if you do, this is the command for that:
```
echo 'unset UBUNTU_MENUPROXY' | sudo tee /etc/X11/Xsession.d/81ubuntu-menu-proxy
```Regards.

---

