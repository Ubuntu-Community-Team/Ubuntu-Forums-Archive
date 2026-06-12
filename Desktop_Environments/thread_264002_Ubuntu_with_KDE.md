---
title: "Ubuntu with KDE"
date: 2006-09-24
forum: Desktop Environments
---

### Post by Bud P on 2006-09-24
Hi everyone:

I am tearing my hair out (what little I have) 
Installed Ubuntu a few weeks ago and then decided to try KDE I like it pretty good except the ICONS on the desktop have some kind of funky font and I cannot figure out how to change it.
The next thing is that the Icons in the toolbar are almost invisable but when I mouse over them the explanation for them comes up ok.
I also cannot figure out how to configure wine, is there a frontend for wine?
Any help on any of these problems would be appriciated.
This is a standalone linux machine.

Bud P

---

### Post by wieman01 on 2006-09-24
_KDE Control Center:_

1) Open a terminal and type "kcontrol". Go to section "Appearance & Themes", then Fonts.
2) Open a terminal and type "kcontrol". Go to section "Desktop", then Panels->Arrangement->Size. Change the size of your taskbar.

_Wine:_

1) XWine: [http://darken33.free.fr/index.php?cat=2&rub=21]("http://darken33.free.fr/index.php?cat=2&rub=21")

---

### Post by Bud P on 2006-09-24
wieman01
Thanks for the quick reply, I will give these a try.
Have a good day

Bud P

---

### Post by Bud P on 2006-09-26
Well I have not been able to change the fonts on the desktop icons or even change the icon itself.
I have worked pretty hard at it to no avail.
I have set everything to default and then changed everything one step at a time within the system settings and have not changed the desktop icons at all.
It should not be this difficult to do one small thing.

any other advice?

Bud P](*,)

---

### Post by wieman01 on 2006-09-26
You can change your Icon Theme under section "Appearance & Themes". See screenshot.

These are MAC OS icons that I like most: [http://www.kde-look.org/content/show.php?content=16564]("http://www.kde-look.org/content/show.php?content=16564")

Another one: [http://www.kde-look.org/content/show.php?content=38467]("http://www.kde-look.org/content/show.php?content=38467")

Hope this does the job.

---

### Post by Bud P on 2006-09-27
I really appriciate the time and effort you are putting in to help me out.
No matter what icon theme that I highlight and apply the icons on the desktop do not change. I am beginning to think that my KDE install is scrambled up somewhere.
I am not going to give up, I am a very stubborn person.:D 

Bud P

---

### Post by wieman01 on 2006-09-27
Don't worry, glad I can be of help. 

Let's try the following from a terminal windows:
> sudo kcontrol
That opens Konqueror with "super user" authority. I've had a similar problem before... Try this and if it works, I will show you a way we can do away with this annoying feature.

---

### Post by Bud P on 2006-09-27
Well that was a no go, I got a ERROR: communication problem with kcontrol, it probably crashed. I am going to reboot and see if that helps.
Bud P
Well maybe I have a problem that is probably self inflicted. I am still getting a ton of errors going into superuser mode but the kde control center is coming up, but I just noticed that on the splash screen It says my machine is   "I686" which is not correct, have I put on the wrong version of KDE for my machine?
Bud P

---

### Post by wieman01 on 2006-09-27
The try this:
1. Open a terminal
2. The type:
> sudo chown -R <your_user> *
Perhaps some of the config.files are not "owned" by your local user.

---

### Post by Bud P on 2006-09-27
Well I am sorry but I am done for the evening, nothing is going right and I am getting frustrated so It is better that I shut it down and come back in the morning. I edited my last post before this one also

Bud P

---

### Post by Bud P on 2006-09-28
wieman01:
I am sorry that I have taken so long to get back here but had a little emergency in the family that I had to attend to.
5 items come into view with the command that you gave me, all of them were finished with the statement "operation not permitted" 
I think that this is because I am not the root user as I had no password prompt in the terminal window nor did it ever ask for my password. 
I think some of the problem is the dumbo behind the keyboard.:( 
One other thing strange is if I open shell - Konsole and input su it asks for my password, when I type in my password I get a authentication error.

Bud P

---

### Post by wieman01 on 2006-09-28
Are you saying that you entered the exact same command & yet you get a permission error?
> sudo chown -R <your_user> *
Usually your initial user - that Ubuntu creates for you - has "super-user" capability when the prefix "sudo" is used. Does the system ask you for a password when you run this command in a terminal?

"su" is disabled by default. Let's tackle that later. "sudo" should - by all means - do.

---

### Post by alcamus on 2006-09-28
This is off-topic, but like the originator of the post, I'm looking for a KDE boost. The question is pretty simple. How do you get the trash can to appear on the desktop? I can't seem to get it off the taskbar. Any information would be of great help.

---

### Post by Bud P on 2006-09-28
I am glad you have not lost patience with me.
 Does the system ask you for a password when you run this command in a terminal?
No.
 sudo chown -R <your_user> * the only way I can get this to work at all is replace <your_user> with my user name which is bud and leave off the brackets.

Bud P

---

### Post by wieman01 on 2006-09-28
> **alcamus said:**
> This is off-topic, but like the originator of the post, I'm looking for a KDE boost. The question is pretty simple. How do you get the trash can to appear on the desktop? I can't seem to get it off the taskbar. Any information would be of great help.
This is indeed off-topic. Please open up a new thread & post your problem. Plus please read the forum guidelines before you do so. Capturing threads is not considered the politest thing to do...

---

### Post by wieman01 on 2006-09-28
> sudo chown -R bud *
That's the right command. Leave out the brackets. The system does not ask you for your password at all? If not, then we have a problem. What's the output?

Don't worry, I seldom lose my patience. :-)

---

### Post by Bud P on 2006-09-28
" sudo chown -R bud * "
well I dont know what has happend now when inputting the command nothing happens.
I am not sure that this worth all the problems that I am having, what do you think about me just uninstalling KDE desktop and doing a reinstall? I am having some other problems also but I just like to tackle things one at a time. I am going to reboot and see if that helps. this is a new problem.

Bud P

---

### Post by Bud P on 2006-09-28
Well I rebooted the machine and giving the command it now asks for my password, typed in my password and got no reply it just went back to the prompt.

Bud

---

### Post by wieman01 on 2006-09-28
If nothing has happened than it is likely that the system has recognized the command. It is possible that you have entered the "sudo" command a few minutes earlier for some other stuff, that's why the system would not ask you again for it (usually there is a 15-min grace period).

Now try to change things in Konqueror... Does it work?

Avoid a fresh install if possible. Wastes your time even more.

---

### Post by wieman01 on 2006-09-28
> **Bud P said:**
> Well I rebooted the machine and giving the command it now asks for my password, typed in my password and got no reply it just went back to the prompt.

Bud
Now fire up the Control Center ("kcontrol") and to the necessary changes. Do they stick?

---

### Post by Bud P on 2006-09-28
> Now try to change things in Konqueror... Does it work?

Nope, you are right about the reinstall I had a real hard time getting some of the video stuff going but I learned a lot.

Bud

---

### Post by wieman01 on 2006-09-28
> kcontrol
They changes still don't stick? D@#$ it. I need to check it out when I get back home... No idea what's going on.

---

### Post by Bud P on 2006-09-28
>  D@#$ it.
That is a lot nicer word than I have been using.;) 

Have a good evening and thank you.

Bud P

---

### Post by wieman01 on 2006-09-28
One LAST thing (next to good night): I tried running 'kcontrol' as 'sudo' last night on my PC and it worked. There is something wrong with your install I reckon. I did this:
> sudo kcontrol
See you tomorrow.

---

