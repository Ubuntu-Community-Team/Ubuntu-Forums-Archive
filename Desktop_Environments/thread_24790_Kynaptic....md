---
title: "Kynaptic..."
date: 2005-04-08
forum: Desktop Environments
---

### Post by Yeeha on 2005-04-08
First of all i just madly like Kubantu.But i have one great problem - it seems Kynaptic is not fully ready or it relies to some other program for adding repositoryes and universe.What should i do, install synaptic?

---

### Post by audax321 on 2005-04-08
not sure what  you mean, but I think you can install Synaptic if you want to... but you could also edit sources by just opening /etc/apt/sources.list as root and editing.

I think the terminal command for KDE would be:

sudo kedit /etc/apt/sources.list

Personally, I think editing the file directly is a lot faster... but thats just me :)

(btw, I use Ubuntu, so take this with a grain of salt)

---

### Post by p!=f on 2005-04-08
Enable universe in /etc/apt/sources.list...
```

sudo kedit /etc/apt/sources.list

```
Just uncomment the line with universe mentioned and run 
```

sudo apt-get update
sudo apt-get install kynaptic

```
I can install Kynaptic w/o a problem.

---

### Post by lao_V on 2005-04-08
[QUOTE=p!=f]Enable universe in /etc/apt/sources.list...
```

sudo kedit /etc/apt/sources.list

```
Just uncomment the line with universe mentioned and run 
```

sudo apt-get update
sudo apt-get install kynaptic

```
I can install Kynaptic w/o a problem.[/QUOTE]

I think Yeeha wants to install synaptic as he's already got kynaptic by default

---

### Post by p!=f on 2005-04-08
[QUOTE=lao_V]I think Yeeha wants to install synaptic as he's already got kynaptic by default[/QUOTE]
Ouch...
<beating a wall with my head> ;)

---

### Post by lao_V on 2005-04-08
[QUOTE=p!=f]Ouch...
<beating a wall with my head> ;)[/QUOTE]

Please don't hurt the wall :-)

---

### Post by Yeeha on 2005-04-08
i dont like doing things from konsole usually so i think i will take synaptic for kynaptic. Kynaptic needs some polishing(repository adding, default download window size such that i user can see buttons).And thx for help and tips.

---

### Post by lao_V on 2005-04-08
[QUOTE=Yeeha]i dont like doing things from konsole usually so i think i will take synaptic for kynaptic. Kynaptic needs some polishing(repository adding, default download window size such that i user can see buttons).And thx for help and tips.[/QUOTE]

Yes kynaptic is only in development stage at the moment hence it lacks quite a few features. Hopefully in the next kde release there should be a fully fledged kynaptic!

---

### Post by Jagasian on 2005-04-08
I have been using Fedora for years now, along with apt for RPM and synaptic.  I personally think that kynaptic can do better than synaptic.  It needs a quick search text box to make searching more obvious and accessible, it also needs repository management, and the ability to list the details of a package, such as its description and dependencies.

With regards to repository management, it would be nice if KDE recognized repository references, as it does for other kinds of URLs.  That way somebody could browse to a page that makes a very small number of packages available via apt, and all that would be required would be to click on a repository URL in konq, which would bring up a dialog asking to add the repository to your list of repositories.

**BUGS:** 
I also noticed a few bugs.  One of the more annoying bugs is when I apply the changes, the dialog window that pops up is too small to display the "continue" button at the bottom of the window, which requires manually resizing the window to see the button.

---

### Post by F for Fragging on 2005-04-09
[QUOTE=p!=f]Enable universe in /etc/apt/sources.list...
```

sudo kedit /etc/apt/sources.list

```
Just uncomment the line with universe mentioned and run 
```

sudo apt-get update
sudo apt-get install kynaptic

```
I can install Kynaptic w/o a problem.[/QUOTE]

I've tried that but it gives me this:

sander@boven:~$ sudo kedit /etc/apt/sources.list
sudo: kedit: command not found

I've just installed Kubuntu a few hours ago, and I didn't uninstall anything, certainly not kedit. What can be wrong?

---

### Post by p!=f on 2005-04-09
[QUOTE=F for Fragging]I've tried that but it gives me this:

sander@boven:~$ sudo kedit /etc/apt/sources.list
sudo: kedit: command not found

I've just installed Kubuntu a few hours ago, and I didn't uninstall anything, certainly not kedit. What can be wrong?[/QUOTE]
You don't have kedit installed. Replace kedit above with your favorite editor if you use something else.

---

### Post by F for Fragging on 2005-04-09
Hmm, since you mentioned kedit, I thought it was installed by default?

Anyway, I tried kate, but it gives me this:

sander@boven:~$ sudo kate /etc/apt/sources.list
Password:
Error: "/var/tmp/kdecache-sander" is owned by uid 1000 instead of uid 0.
Link points to "/var/tmp/kdecache-root"
kate: ERROR: Communication problem with kate, it probably crashed.
sander@boven:~$

When I try to open Kate from the K Menu, it appears as if it's loading in taskbar for some time, but then it disappears again and nothing happens.

I have the idea that Kubuntu is still a bit bugged.

---

### Post by p!=f on 2005-04-09
[QUOTE=F for Fragging]Hmm, since you mentioned kedit, I thought it was installed by default?

Anyway, I tried kate, but it gives me this:

sander@boven:~$ sudo kate /etc/apt/sources.list
Password:
Error: "/var/tmp/kdecache-sander" is owned by uid 1000 instead of uid 0.
Link points to "/var/tmp/kdecache-root"
kate: ERROR: Communication problem with kate, it probably crashed.
sander@boven:~$

When I try to open Kate from the K Menu, it appears as if it's loading in taskbar for some time, but then it disappears again and nothing happens.

I have the idea that Kubuntu is still a bit bugged.[/QUOTE]
Don't you run KDE as root?
Try sudo nano -w /etc/apt/sources.list for command line editor.

---

### Post by bistrototal on 2005-04-09
I just installed Kubuntu and it so far so good, but when i tried to run kynaptic, my root password doesn't work. I created a root user in the installation and when i do 'su -' in konsole it's no problem.

Is there a simple solution to this?

Thanks,

---

### Post by p!=f on 2005-04-09
[QUOTE=bistrototal]I just installed Kubuntu and it so far so good, but when i tried to run kynaptic, my root password doesn't work. I created a root user in the installation and when i do 'su -' in konsole it's no problem.

Is there a simple solution to this?

Thanks,[/QUOTE]
And if you run
```

sudo kynaptic

```
from the KDE terminal? Does it work? 
You might want to use 
```

sudo -s

```
to get a root prompt. You don't need to have root password enabled which I think is the advantage over the su solution.

---

### Post by bistrototal on 2005-04-09
When i run 'sudo kynaptic' i'm told that my user 'is not in the sudoers file.' I then added my user to /etc/sudoers and now it works fine! Thanks! :-D 

But i find it odd that i must use my user's password to run kynaptic from the menu and not the root password. Is there a way to change this behaviour?

---

### Post by F for Fragging on 2005-04-09
[QUOTE=p!=f]Don't you run KDE as root?
Try sudo nano -w /etc/apt/sources.list for command line editor.[/QUOTE]
 Thank you very much p=!f, nano worked for me.

Another strange thing is that when I rebooted and logged in again, Kate asked for my root password and started itself automatically? Very weird...

BTW, the way Ubuntu implements root is very confusing for me. I read this - [http://www.ubuntulinux.org/wiki/RootSudo](http://www.ubuntulinux.org/wiki/RootSudo) - then I entered a root password, then I tried to log out of my normal user account and log in with my user account (like I always did on Fedora Core 3, my previous distro) but then I found out that root logins aren't possible?

So I understand that if I need root acess I should use sudo. But what do you exactly mean with "running KDE as root" then?

---

### Post by p!=f on 2005-04-09
[QUOTE=F for Fragging]Thank you very much p=!f, nano worked for me.

Another strange thing is that when I rebooted and logged in again, Kate started itself automatically? Very weird...
[/quote]
Seems like you logged out with kate opened and you saved your session. Note that I'm not KDE user so I might be wrong but there's an option in GNOME when you log out to save your session so (almost) any program you let opened will be opened again during next login. Something similar will be in KDE as well.
If you can't dig it, start a new tread in the Kubuntu forum.
[QUOTE=F for Fragging]
BTW, the way Ubuntu implements root is very confusing for me. I read this - [http://www.ubuntulinux.org/wiki/RootSudo](http://www.ubuntulinux.org/wiki/RootSudo) - then I entered a root password, then I tried to log out of my normal user account and log in with my user account (like I always did on Fedora Core 3, my previous distro) but then I found out that root logins aren't possible?

So I understand that if I need root acess I should use sudo. But what do you exactly mean with "running KDE as root" then?[/QUOTE]
Ubuntu, by default, does not use root account at all. If a command needs root privileges you just add sudo <command>. If you want root prompt you use sudo -s or sudo -i for a full root environment.
All users which want to use sudo must be specified in /etc/sudoers file. This is added by default for the account you created during installation. If you create another user account and you want her to use sudo, you has to add an entry there. To lock root account type sudo passwd -l root.
That's all sudo magic. :)

If you enable root and login as root you may start KDE under root privileges but it's not Good Idea(TM) at all.

---

### Post by dermotti on 2005-04-09
Honestly, i hate Kynaptic, I use Kpackage, much better imho.

---

### Post by lao_V on 2005-04-09
Try KWrite instead of Kedit or open up konqueror and browse to the folder /etc/apt/ and then right click on sources.list and chose actions -> edit as root

---

### Post by bistrototal on 2005-04-09
Just installed KPackage and it seems very good!

Thanks for the tip!

---

### Post by Yeeha on 2005-04-09
Someone should make sticky post about how to enable root, i did it according to to some tip i found i dont remember where.I think those who have worked with other linuxes would like su. I like sudo when there is needed root rights shortly(for one command) but su when i mess with things that require it.

---

### Post by lao_V on 2005-04-09
It is extremely easy to enable root: [b]sudo passwd root
[/b]Doing a search on "how to enable root" will bring plenty of results

---

### Post by Jonathan2007 on 2005-04-10
So I downloaded Kpackage because Kynaptic won't open for me. Yes I have rebooted and I think it is just that buggy. So anywho I tried to install something using Kpackage and it wanted to use su. I tried my password but it didn't work. I though maybe I need to set the root account password even if it isn't enabled. I tried to do it using Kuser and it just crashed. So I am going to try to enable the root account using what was suggested. So am I correct in assuming Kpackage needs to use su and not sudo and wants the root account enabled? Also would use suggest using Kpackage over Synaptic or what should I use instead of Kynaptic (because it is a piece of crap that I refuse to use)? I don't much like Kpackage because it checks if there are new packages each time I open it and since I added all the repositories recommended by unbuntuguide.org it has to check a lot of stuff and takes a while. Please keep in mind that I am a Linux newb and would prefer a GUI over apt-get (although I am getting use to apt-get and like it). Thanks

---

### Post by t0dzilla on 2005-04-10
> I've tried that but it gives me this:
 
 sander@boven:~$ sudo kedit /etc/apt/sources.list
 sudo: kedit: command not found 

you could substitute nano...

this is what i did and it worked just fine. 
synaptic is leaps and bounds more betterer. :)

---

### Post by Jonathan2007 on 2005-04-10
[QUOTE=t0dzilla]you could substitute nano...

this is what i did and it worked just fine. 
synaptic is leaps and bounds more betterer. :)[/QUOTE]
Is it better than Kpackage? Is it bad if I use Synaptic in Kubuntu (since it is a gnome app)?

---

### Post by dermotti on 2005-04-10
nano is a command line text editor

---

### Post by p!=f on 2005-04-11
[QUOTE=t0dzilla]you could substitute nano...

this is what i did and it worked just fine. 
synaptic is leaps and bounds more betterer. :)[/QUOTE]
Do you even bother to read the posts here?

---

### Post by huh? on 2005-04-11
just checked myself..kedit is not installed, but I started with Ubuntu, I had gedit installed...apt-get oughta do the trick for you

---

### Post by segrewb on 2005-04-18
[QUOTE=Jonathan2007]Is it better than Kpackage? Is it bad if I use Synaptic in Kubuntu (since it is a gnome app)?[/QUOTE]

I use Synaptic in Kubuntu with no problems.  Just use apt-get or Kynaptic or Kpackage to add it.  

Segrewb :)

---

### Post by Gezzer on 2005-04-18
[QUOTE=segrewb]I use Synaptic in Kubuntu with no problems.  Just use apt-get or Kynaptic or Kpackage to add it.  

Segrewb :)[/QUOTE]
 thats what i did 
i added synaptic
then ticked universe
and now kynaptic works with it as well ...

---

### Post by brk3 on 2005-04-19
The only problem I have with kynaptic is that it doesnt have a description display for the package you have selected. So you dont know what your installing!
Other than that its great though, Im sure theres features lined up for the next realease :)

---

### Post by ltmon on 2005-04-19
[QUOTE=brk3]The only problem I have with kynaptic is that it doesnt have a description display for the package you have selected. So you dont know what your installing!
Other than that its great though, Im sure theres features lined up for the next realease :)[/QUOTE]

It does have the short description, but it's implemented as a tool-tip, which is really crappy from a UI point of view (I don't know what the developer must have been thinking).  Just hover on the package name to get a short description.

L.

---

### Post by carney1979 on 2005-05-23
I can live with Kynaptic, but I do have one concern......

If I am installing a package that requires some user interaction to make configuration choices during the install, will Kynaptic pop up a window or something like Synaptic does?

David

---

### Post by dinges on 2005-07-20
> Anyway, I tried kate, but it gives me this:

sander@boven:~$ sudo kate /etc/apt/sources.list
Password:
Error: "/var/tmp/kdecache-sander" is owned by uid 1000 instead of uid 0.
Link points to "/var/tmp/kdecache-root"
kate: ERROR: Communication problem with kate, it probably crashed.
sander@boven:~$

When I try to open Kate from the K Menu, it appears as if it's loading in taskbar for some time, but then it disappears again and nothing happens.

I have the idea that Kubuntu is still a bit bugged.

I know, my answer is a bit late for this post, but I had the above error and found this discussion. I solved it. The solution is not to use 'sudo' but 'kdesu' and then all works as expected.

---

