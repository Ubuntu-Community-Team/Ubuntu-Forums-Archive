---
title: "[SOLVED] aMSN"
date: 2008-02-29
forum: Desktop Environments
---

### Post by talib on 2008-02-29
Hello every one
this is my first post in here, 
I want to install aMSN and am getting the follewing error... 
thank you in advance for helping me  



[COLOR="Red"]The following packages have unmet dependencies:
  amsn: Depends: tcl8.4 but it is not installable
        Depends: tk8.4 but it is not installable
        Depends: tcltls but it is not going to be installed
E: Broken packages
 [/COLOR]

---

### Post by noXstyle on 2008-02-29
just try: apt-get install tcl8.4 tk8.4 tcltls

if they are uninstallable --> apt-get -f install

if the problem still occurs i suggest manual installation.. just google the packages and build from the source.. thats what i've done when i've used debian etch/lenny. never had problems with those packages in ubuntu. oh, and tcl8.4 requires libc6..

edit: i think the category should've been general help rather than desktop environments...
***: if you havent changed your sources.list repos now its good time to do that.

---

### Post by Zeroangel on 2008-02-29
If the tcl packages *are* uninstallable using the apt-get method. Try using this command
```
sudo aptitude install tcl8.4 tk8.4 tcltls
```
Using aptitude, it will sometimes suggest ways to install the packages (ie: if other packages need to be downgraded) and ask you if you want it to carry out the suggestion.

If you end up having too much problems, then try Emesene. Its a neat little MSN-only messenger prog.

---

### Post by cometa2k7 on 2008-03-20
I had similar problems, 

[LIST]
[*] Completely uninstall aMSN and those packages
[*] Use Synaptic to install aMSN
[*] Select all of the suggested packages
[*] Check to see if those packages are going to be installed, if not, install them.
[/LIST]

Then run aMSN, and you shouldn't have problems.

---

### Post by Claus7 on 2008-03-20
Hello and welcome!

I have made an installation from scratch of amsn 0.98b which is the latest version availabe. If you install the amsn from synaptic probably it will use tcl8.4 tk8.4 which will not enable you to have an eye candy amsn. In other words it might look a little bit slugish. My proposal for ubuntu dapper might be good, yet it is a difficult one for someone who hasn't any experience. 
[http://ubuntuforums.org/showthread.php?t=712425&highlight=amsn](http://ubuntuforums.org/showthread.php?t=712425&highlight=amsn) (Dapper at least) latest from svn (**s**ub**v**ersio**n**)

Other useful posts on the installation of amsn are the following:

[http://ubuntuforums.org/showthread.php?t=297676&highlight=amsn](http://ubuntuforums.org/showthread.php?t=297676&highlight=amsn) (Edgy, Feisty and Gutsy) 0.97
[http://ubuntuforums.org/showthread.php?t=595744&highlight=amsn](http://ubuntuforums.org/showthread.php?t=595744&highlight=amsn) (Gutsy at least) .............. 0.97rc1
[http://ubuntuforums.org/showthread.php?t=621441&highlight=amsn](http://ubuntuforums.org/showthread.php?t=621441&highlight=amsn) (Gutsy) ........................... latest from svn
[http://ubuntuforums.org/showthread.php?t=435338&highlight=amsn](http://ubuntuforums.org/showthread.php?t=435338&highlight=amsn) (Feisty) ........................... 0.97b 
[http://ubuntuforums.org/showthread.php?t=649364&highlight=amsn](http://ubuntuforums.org/showthread.php?t=649364&highlight=amsn) (Gutsy) ........................... 0.97 stable 

and they automate the whole procedure.

Hope this helps,
Regards!

---

