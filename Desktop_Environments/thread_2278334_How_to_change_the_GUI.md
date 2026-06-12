---
title: "How to change the GUI"
date: 2015-05-15
forum: Desktop Environments
---

### Post by mattig89ch on 2015-05-15
Hidy ho everyone,

I was googling around about changing the GUI of ubuntu, and I found a couple of good links on this topic.  I installed the cinnamon ui, and am trying to start that, but there is a step all the links list that I can't find.

All the links I found say to click the little ubuntu icon in the top right of the login screen to change the desktop environment.  But I'm not seeing an ubuntu icon on the top right.

I attached (or tried to attach) a snip of what I see on my login screen.  None of them say anything about changing the environment.  is there another way to change the desktop environment?

[ATTACH=CONFIG]261992[/ATTACH]

---

### Post by Kenneth_Benson on 2015-05-15
Are you sure it says top right and not top left?

---

### Post by mattig89ch on 2015-05-15
just edited the post to show the entire login screen.

And yea, i've seen 3 or 4 links that say to click the icon on the top right. of the screen.  though there is no ubuntu icon in the top left of my screen either.

---

### Post by Kenneth_Benson on 2015-05-15
Ok. I can't help at the moment, at the library on a windows box. I'll check when I get home but I'm nonet on that one so I won't be able to get back to
you till tomorrow. Hopefully, someone else can help you before then.

---

### Post by sudodus on 2015-05-15
Which version of Ubuntu are you running? For example 14.04.2 LTS or 14.10 or 15.04 - things may be different. It says 14.04 in your screenshot - is it up to date with properly installed packages?

There used to be a round clickable symbol near the login box. See the attached picture - but I see no such round symbol in your screenshots.

---

### Post by v3.xx on 2015-05-15
[ATTACH=CONFIG]261995[/ATTACH]

Edit
Hay sudodus :)

---

### Post by mattig89ch on 2015-05-15
according to the info at the bottom of the login screen (which is what I'm going by), this is 14.04 LTS.

The iso image name I have is: "ubuntu-14.04.2-desktop-amd64"

Edit: is there another place to look up what version of Ubuntu I have?

---

### Post by sudodus on 2015-05-15
I got curious and looked at an installed 14.04.2 LTS system, and that clickable symbol near the login box is not there, and I am as lost as you :confused: 			

		
 	
***Whoever reads this and knows how to change between sessions, please chip in and help!***

---

### Post by v3.xx on 2015-05-15
When did that happen?  The desktop is now being locked in?

[http://askubuntu.com/questions/456766/how-to-set-default-session-in-ubuntu-14-04-lts](http://askubuntu.com/questions/456766/how-to-set-default-session-in-ubuntu-14-04-lts)

---

### Post by sudodus on 2015-05-15
Good question. Maybe with 14.04.2 LTS.

Maybe it helps to try with another greeter according to the following link

[https://askubuntu.com/questions/75755/how-to-change-the-lightdm-theme-greeter](https://askubuntu.com/questions/75755/how-to-change-the-lightdm-theme-greeter)

---

### Post by mattig89ch on 2015-05-15
so, the greeter is the login screen?

---

### Post by sudodus on 2015-05-15
After installing 'lightdm-gtk-greeter' and rebooting, that greeter seems to be selected by default, and there is a ***symbol at the top right corner*** (near the shutdown symbol). Click on that symbol to select session.

```
sudo apt-get install lightdm-gtk-greeter
```

Notice that I did ***not*** edit any configuration file (I tried according to the tip in the link in my previous post, but that borked the system).

---

### Post by sudodus on 2015-05-15
> **mattig89ch said:**
> so, the greeter is the login screen? Yes

---

### Post by v3.xx on 2015-05-15
> **sudodus said:**
> Notice that I did ***not*** edit any configuration file (I tried according to the tip in the link in my previous post, but that borked the system).
Borked mine too

---

### Post by v3.xx on 2015-05-15
I'm trying this on lubuntu, gtk-greeter was already installed.

---

### Post by sudodus on 2015-05-15
I think Lubuntu is not affected by this bug. (Let us call it a bug.)

---

### Post by deadflowr on 2015-05-15
I'm not sure cinnamon is available through 14.04 repos.
How'd you install it?

Typically the login screen will give you the options of choosing different session, IF the session has a proper .desktop file in the folder
/usr/share/xsessions.
If it does not have a .desktop file there, then it typically won't show an option.
Most sessions add that file when the particular session is installed.
I'm guessing cinnamon's would be called cinnamon-session.
Do you have that package installed?

---

### Post by v3.xx on 2015-05-15
> **sudodus said:**
> I think Lubuntu is not affected by this bug. (Let us call it a bug.)
I cannot switch to a openbox session, no icon :)  I think this is lightdm.

---

### Post by sudodus on 2015-05-15
I have not installed Lubuntu 14.04 right now, but I have a Wily Lubuntu (to become 15.10), and I can switch sessions with it (also into Openbox) clicking on an icon near the top right corner. I think that it worked when I iso-tested Lubuntu 14.04 LTS, but it was long ago, so I am not 100% sure.

---

### Post by sudodus on 2015-05-15
@ mattig89ch

Did you try according to post #12? I think it is likely to give you options to select session. But if the installation of Cinnamon is not complete, there might be another problem. Then please consider deadflowr's tips in post #17

---

### Post by mattig89ch on 2015-05-15
That I did, and it worked!  I was able to switch environments to cinnamon.  As someone, who doesn't use linux nearly as often as others, this ui is far more familiar as to where things are, and how to access them.

Thanks for the help all!
> **deadflowr said:**
> I'm not sure cinnamon is available through 14.04 repos.
How'd you install it?


I used this link:
[http://www.omgubuntu.co.uk/2014/07/new-cinnamon-ubuntu-14-04-ppa-stable](http://www.omgubuntu.co.uk/2014/07/new-cinnamon-ubuntu-14-04-ppa-stable)

---

### Post by sudodus on 2015-05-15
Congratulations to a working system :KS

If you feel that your problem (presented in the first post) is solved, please click on **Thread Tools** at the top of the page and mark this thread as SOLVED

---

