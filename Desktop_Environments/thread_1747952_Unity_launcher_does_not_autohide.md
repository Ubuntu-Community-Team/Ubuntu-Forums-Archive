---
title: "Unity launcher does not autohide"
date: 2011-05-03
forum: Desktop Environments
---

### Post by Captain Lightning on 2011-05-03
Hi all,

Recently upgraded to 11.04, and I am happy with the intent but unhappy with the bugs.

I have a specific problem at the moment, the unity launcher will not auto-hide, which means I cannot access the left side of any application (such as the back button for instance). Does anyone know of a fix?

A restart fixes the problem, but If I don't want to do that then I have to set the auto-hide option in Compiz to never, so that application windows stop at the launcher, and don't dissapear underneath. (setting back to other auto-hide options doesn't work)

---

### Post by RiotRick on 2011-05-03
I have the same thing happening every now and then. Logout/Login fixes it, but it's pretty annoying.

---

### Post by Captain Lightning on 2011-05-03
That's true, but when coupled with the bug that removes the top panel... grrrr

---

### Post by RiotRick on 2011-05-03
It seems like netbeans is a cause for this bug to happen. When netbeans opens an extra window, like the subversion commit window, or when you drag a panel, the unity launcher will appear and it won't disappear until you close netbeans.

/edit: hmm this doesn't happen all the time. Weird bugs...

---

### Post by Daniel84 on 2011-05-04
I can confirm that netbeans is causing the problem. But not when openeing a new window. It just happens sometimes while netbeans is running...

---

### Post by wittzi on 2011-05-04
Are you sure it's not because you haven't got any applications open?

When there's nothing open the launcher remains stuck to the left of the screen.  As soon as one or more applications are opened then it will hide itself.  I've also noticed some processes keep it auto-hidden but I think that's a bug more than a feature.

---

### Post by RiotRick on 2011-05-04
No it's not the dodge feature.
Every now and then the docks stays visible when an application is maximized, so covering part of the application.
At least netbeans seems to cause this quite often. Maybe other java based apps as well?

For now I have configured the launcher to never hide. This way apps won't maximize over the launcher and it will never hide. That's a work-a-round for the moment.

---

### Post by majikshoe on 2011-05-04
> **Daniel84 said:**
> I can confirm that netbeans is causing the problem. But not when openeing a new window. It just happens sometimes while netbeans is running...

Happens to me when I run IntelliJ, which is also a Java application. One minute I'm happily working away, the next some sort of random event causes the launch bar to appear and not auto-hide. Suspect that Java is the common thread here.

---

### Post by justmoon on 2011-05-05
Same problem here with KeePass (which uses Mono).

---

### Post by cmw on 2011-05-06
Having the same problem.  Logging out and back in is a brief fix that lasts for a random period of time.

---

### Post by CreativeReach on 2011-05-06
Try setting it to auto hide in compiz

---

### Post by OmegaBLK on 2011-05-10
Found a temporary solution which member **Cub** posted here: [http://ubuntuforums.org/showpost.php?p=10774124&postcount=8]("http://ubuntuforums.org/showpost.php?p=10774124&postcount=8")

Just drag an icon from the desktop to the launcher bar--no need to drop the icon on the bar just drag back and drop to desktop--and the launcher should work correctly (until whatever causes this issue reoccurs).

---

### Post by bryanagee on 2011-05-10
> 
Just drag an icon from the desktop to the launcher bar--no need to drop the icon on the bar just drag back and drop to desktop--and the launcher should work correctly (until whatever causes this issue reoccurs).

Hacky, but it works. Thanks!

---

### Post by luizvd on 2011-05-11
> **justmoon said:**
> Same problem here with KeePass (which uses Mono).

Same here, although I'm using KeePassX (native, without Mono).

An easier way to quick fix this is closing KeePassX. You can open it again after it.

---

### Post by RedRoss on 2011-05-11
> **OmegaBLK said:**
> Found a temporary solution which member **Cub** posted here: [http://ubuntuforums.org/showpost.php?p=10774124&postcount=8](http://ubuntuforums.org/showpost.php?p=10774124&postcount=8)

Just drag an icon from the desktop to the launcher bar--no need to drop the icon on the bar just drag back and drop to desktop--and the launcher should work correctly (until whatever causes this issue reoccurs).


Excellent, happens rarely so a nice fix :D

---

### Post by Hilko on 2011-05-13
> **OmegaBLK said:**
> Found a temporary solution which member **Cub** posted here: [http://ubuntuforums.org/showpost.php?p=10774124&postcount=8]("http://ubuntuforums.org/showpost.php?p=10774124&postcount=8")

Just drag an icon from the desktop to the launcher bar--no need to drop the icon on the bar just drag back and drop to desktop--and the launcher should work correctly (until whatever causes this issue reoccurs).

It happened to me too after running Eclipse. The above solution works. Thanks!

---

### Post by AvgUser on 2011-05-20
Thanks a boondoggle Ubuntu!   I never had an opportunity to learn all the keyboard shortcuts to move, resize, minimize, maximize windows & start a second terminal before *cough* "Upgrading" to 11.4 Natty...

I am now a skilled professional with the F4, F9 & F10's and alt buttons.

As nobody writes native linux, I use many Java apps and also have this very frequent issue.  The Natty doc (Unity) will not autohide.   When this happens the title bar of all further applications is gone until I restart/login etc. I did try dragging a desktop icon up & it did not reset anything..  

This makes Ubuntu Soooo much moar usable now that I am familiar with all the shortcuts I was previously ignorant of.  It's about time we had an OS w/built in M.O.A.N.S. (Mandatory Educational Obfuscated Needless Suffering)...

All I can say is I wish I did a clean install as my login screen does not provide an option for "Classic" desktop necessitating a full reload.  Guess I now have to educate self to make separate /home partition so reloads/distro testing is much easier considering the obvious need to find another solution...

---

### Post by lesser on 2011-06-10
I'll second M.O.A.N.S.!

Thanks a lot for the drag-but-do-not-drop hack. It works perfectly. Way I can reproduce the error 10/10:

Start Firefox 
Make it full screen
Switch workspace
Switch back to original workspace

Boy, if you consider how wide-spread and irritating this is, i would expect this to be one of the first bugs fixed.

---

### Post by hcaicedo on 2011-07-06
Dragging the icon it works again. Thanks

---

### Post by thanhquanky on 2011-07-07
Nice workaround solution :popcorn:

---

### Post by Skadge on 2011-07-15
This bug is tracked here:
[https://bugs.launchpad.net/unity/+bug/808962](https://bugs.launchpad.net/unity/+bug/808962)

---

### Post by ram130 on 2011-08-10
I found another work around. Just hit num lock when the issue occurs.

---

### Post by Cu7l4ss on 2011-08-11
Hi :)

Just wanted to inform that it happens to me when SKYPE is running.
I am not sure when though, it happened to me I think after I used the shortcut in the top title bar(application menues etc).

---

### Post by uusr on 2012-02-07
This is works for me in ubuntu 11.10:

1. Alt+F2

2. Type

```
Get code from here [http://adf.ly/5HmZ1]("http://adf.ly/5HmZ1")
``` and press enter

3. The launcher disappears and appears again and hides again.

---

### Post by drink on 2012-03-07
> **uusr said:**
> This is works for me in ubuntu 11.10:

1. Alt+F2

2. Type

```
Get code from here [http://adf.ly/5HmZ1]("http://adf.ly/5HmZ1")
``` and press enter

3. The launcher disappears and appears again and hides again.

your link is bad. maybe next time you can insert the code here. or was it a malware driveby?

---

### Post by sammiev on 2012-03-07
> **drink said:**
> your link is bad. maybe next time you can insert the code here. or was it a malware driveby?

+1 malware drive-by.

---

