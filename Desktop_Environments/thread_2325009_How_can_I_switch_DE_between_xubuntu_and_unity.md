---
title: "How can I switch DE between xubuntu and unity?"
date: 2016-05-18
forum: Desktop Environments
---

### Post by james_xu2 on 2016-05-18
I installed xubuntu and then I want to switch back to the default unity DE, ideally I intend to swith beteen those two kind of DE smoothly. How can I do that?

The ubuntu I installed is 16.04 LTS. By now, everytime, when I boot up, it will show a login screen from xubuntu. 

Thanks in advance

---

### Post by sudodus on 2016-05-18
At the login screen you select ***session*** (and the session can be Unity for standard Ubuntu, Xubuntu-desktop for Xubuntu or XFCE (for 'only' XFCE without the Xubuntu tweaks, and maybe some other alternatives too).

---

### Post by james_xu2 on 2016-05-18
@sudodus,actually, there is not any choice persencing on xubuntu login screen,so I can do nothing.

---

### Post by sudodus on 2016-05-18
At the login screen of Xubuntu 16.04 LTS, near the top right corner (on the panel), there is a round button with a mouse head (when set to use Xubuntu). Click on it and select another session, when you want to switch to Ubuntu with Unity.

I think you find something similar in previous versions of Xubuntu's login screen.

---

### Post by egeezer on 2016-05-18
Did you install Ubuntu and then install xubuntu-desktop, or did you install from the Xubuntu ISO?  If you did the latter, you won't have the Unity option.

---

### Post by vasa1 on 2016-05-18
I think what OP means is that the *appearance* of the screen (grub/spash/greeter/logut/etc) is that of Xubuntu and not that of Unity. I think OP doesn't mean logging into, and using, Unity isn't possible.

james_xu2, please post the contents of ```
ls /usr/share/xessions
```and please use [CODE] tags whenever posting terminal output.

---

### Post by james_xu2 on 2016-05-20
@[COLOR=#c61919]vasa1, do you refer to xsessions?[/COLOR]

james@james-VirtualBox:~$ ls /usr/share/xessions
ls: cannot access '/usr/share/xessions': No such file or directory

james@james-VirtualBox:~$ ls  /usr/share/xsessions
ubuntu.desktop  xfce.desktop  xubuntu.desktop

@all, things are changed by unknown reason.

Now, when I login, it show a xubuntu login screen,after I login it go into a unify de.
[IMG]http://thumbnail0.baidupcs.com/thumbnail/6afd2dd5138cb16cd1700709c272d929?fid=1443129017-250528-701191520374193&time=1463720400&rt=sh&sign=FDTAER-DCb740ccc5511e5e8fedcff06b081203-o%2F9aN5fj2R3R%2BvOTh4yBt36O6LM%3D&expires=8h&chkv=0&chkbd=0&chkpc=&dp-logid=3260290652632010699&dp-callid=0&size=c710_u400&quality=100[/IMG]

[IMG]http://pan.baidu.com/s/1bRMxci[/IMG]
[IMG]http://thumbnail0.baidupcs.com/thumbnail/389607a3d7d371b624d450fc1ebf05cb?fid=1443129017-250528-795612882115717&time=1463720400&rt=sh&sign=FDTAER-DCb740ccc5511e5e8fedcff06b081203-BPR8FA90k62s0nRi8fKcxK66Kw4%3D&expires=8h&chkv=0&chkbd=0&chkpc=&dp-logid=3260314128910730648&dp-callid=0&size=c710_u400&quality=100[/IMG]
there are two target I wanted.
1. login to unify directly.
2. swtich between unify and xbuntu de.

Any helps are appreciated. Thanks in advance.

---

### Post by sudodus on 2016-05-20
- Click on the symbol, that I marked in the attached file to change session (Unity or Xubuntu). When Xubuntu is/was selected, there will be a mouse head, when Unity is/was selected, there is an Ubuntu logo (like it is now in the attached file).

- After clicking on the symbol, a pull-down menu appears. Select session in the pull-down menu.

Finally, log in :-)

---

### Post by CantankRus on 2016-05-20
@** james_xu2**
Your first pic shows lightdm using the **lightdm-gtk-greeter** (Xubuntu default)
The default greeter for Ubuntu is the **unity-greeter**.

When you installed Xubuntu the **lightdm-gtk-greeter** became the greeter.
Solution....remove **lightdm-gtk-greeter** and lightdm will revert to using the **unity-greeter**.
```
sudo apt-get remove lightdm-gtk-greeter
```
It may say **xubuntu-desktop** is to be removed.
You can ignore this as xubuntu-desktop is just a [**_[COLOR="#B22222"]meta-package[/COLOR]_**]("https://help.ubuntu.com/community/MetaPackages") and does not contain any actual software, it simply depends on other packages to be installed. 

Reboot and you should see the unity-greeter.
Chose your session by clicking on the logo to the right.

---

### Post by james_xu2 on 2016-05-20
Thank @sudodus, what your said is correct, I can switch xbuntu or unify freely now.
Thanks all of your guys.

---

### Post by vasa1 on 2016-05-20
You can mark your thread solved. Visit [https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads) to know how and why :)

---

