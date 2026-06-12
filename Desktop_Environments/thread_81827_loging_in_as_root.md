---
title: "loging in as root"
date: 2005-10-25
forum: Desktop Environments
---

### Post by daddario on 2005-10-25
I have this problem: I cant log in as root user, if I try to logon as root in the logon screen, wath comes  after booting it says> administrators cant log on from here (thaths normal rigth?) and after loging on as non-root-user and opening *run as difrent user* nothin happens, if I try to typr in the command line > sudo chown  x / again still nothing happens (let's say , thath my username is x ) I need to configure my HD , I cand write on it...

I hope you understand me.
I'm sorry four...
...stupid question
...bad english

And a problem wath is not so important... I cnt get estonian keyboard layout.
BTTW> I had same trouble with Knoppix
daddario.

---

### Post by kurtkraut on 2005-10-25
You are blocked to login straight as root for security issues. If you need to do a task as root, just use in your terminal:

```
sudo wanted command
```

---

### Post by zekolas on 2005-10-25
For security reasons most debian based distro's have the root account disabled. Everything is done through the "sudo" command.

---

### Post by daddario on 2005-10-25
after typeing in command line> sudo wanted command   it replys > wanted: command not found.


EDIT> damn im an idiot

---

### Post by GeneralZod on 2005-10-25
[QUOTE=daddario]after typeing in command line> sudo wanted command   it replys > wanted: command not found.[/QUOTE]

No, he means that you should type "sudo" before typing the command you want to run as root.  So, for example, if you want to run "nano /etc/X11/xorg.conf" as root, you would do:

```

sudo nano /etc/X11/xorg.conf

```

entering your usual user password if you are asked for one.

Hope this helps,
Simon :)

---

### Post by daddario on 2005-10-25
yes I understand it (;  but still how can I make users allow to read,write,execute my hd ?

---

### Post by rickwood on 2005-10-25
If you want to log in as root, here's what you can do:

1.  You need to set a password for the root account.  In a terminal window type:
 
```
sudo passwd
```
 
2.  Now that the root account is set up with a password, you can log in as root.  However, you can't do this from the gdm screen.  So, this is what I do.  Switch to a console by pressing Alt-F1.  Login as root.  Now, kill gdm:
 
```
killall gdm
```
 
3.  Now start X:
 
```
startx
```
 
4.  When you're done, log out of X/gnome.  This will take you back to the console prompt.  Now restart gdm and you can log in as a normal user again:
 
```
gdm
```
 
I'm sure there are numerous other ways to do this too, but this seems to work for me.

---

### Post by aysiu on 2005-10-25
Just read this:

[https://wiki.ubuntu.com/RootSudo](https://wiki.ubuntu.com/RootSudo)

---

### Post by daddario on 2005-10-26
yes I have made thadh root password earlier.....
if I type in terminal>
```
killall gdm
```

it says>
```
gdm(5516): Operation not permitted
gdm(5527): Operation not permitted
gdm: no process killed
```





EDIT> if I press alt+f1  the apllications(the first bar, I m not sure is thath applications, I put estonian *version*) bar opens

---

### Post by daddario on 2005-10-26
now, I got loged in as root, but still cannot change my hd permissions... if i try to chnge them it says> sorry, cannot change *fiilesystem* permissions.
note> I translate it from estonian... in english *version* it could be said diffrently.

Wath is going on?


I THINK I got it....   confiqure seperate directories(cataloques)...

---

### Post by Revert on 2005-10-26
Could someone please explain what some of the security implications of logging in as root are?  I'm a new user and still adjusting to Linux, so, if possible, I'd like to know.

---

### Post by Hallavej on 2005-10-26
[QUOTE=daddario]now, I got loged in as root, but still cannot change my hd permissions... if i try to chnge them it says> sorry, cannot change *fiilesystem* permissions.
note> I translate it from estonian... in english *version* it could be said diffrently.

Wath is going on?


I THINK I got it....   confiqure seperate directories(cataloques)...[/QUOTE]


"sudo chmod" is your friend. Eg. "sudo chmod 755 filename" chances the permisions to rwx-xr-xr. See man chmod for details. You can also change them with nautilus if you start it with "sudo nautilus"

---

### Post by zekolas on 2005-10-26
[QUOTE=Revert]Could someone please explain what some of the security implications of logging in as root are?  I'm a new user and still adjusting to Linux, so, if possible, I'd like to know.[/QUOTE]

well as root you have full control over the entire system. So lets say you accedently run a malicious program, it has free reign over the entire system. Maybe you download a virus and it brings down the system, maybe the program is a back door that allows some unauthorised access(who then will have root access to the whole system). 

Also security bugs do exist in linux, lets say firefox/gaim/gftp(or whatever program) has a bug in it allowing unauthorised access to the system, if your running the program as root, the intruder will then have root access as well.

However if your logged in as a user and download a virus, or some program with a security problem, the virus/intruder will only have access to the files that the user has access too, and would not be able to do much damage to the wider system. This applies more to multiuser systems, since each user cannot access the other users files.

---

### Post by daddario on 2005-11-03
Did'nt make a new thread... I put ed ubuntu on another computer. Now how can I do thath I can log in not from the pretty login screen, but from command line( don't know is it the rigth word). 
alt+f1 opens only applications bar.

---

### Post by just_another_lamer on 2005-11-03
[QUOTE=kurtkraut]You are blocked to login straight as root for security issues. If you need to do a task as root, just use in your terminal:

```
sudo wanted command
```[/QUOTE]

cant use "sudo", its asked for password and then says "Sorry, try again" :( 
"su" works with same password

---

### Post by daddario on 2005-11-03
do you even have a root account? if not, open terminal & type> ```
sudo -s -H
``` and now make up an password and type it.

---

### Post by daddario on 2005-11-03
[QUOTE=daddario]Did'nt make a new thread... I put ed ubuntu on another computer. Now how can I do thath I can log in not from the pretty login screen, but from command line( don't know is it the rigth word). 
alt+f1 opens only applications bar.[/QUOTE]


and how do I get Wine? I need to run a mikroshoft vindoze program (search for some acrobat files)  ```
sudo apt-get install wine
``` doesent work> ```
Package wine is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package wine has no installation candidate
root@baseilo:~ #

```

---

### Post by domino on 2005-11-03
I guess this is the best thread to post my question. I have enabled root and created a nice long password. I also enabled root login to DGM. I have no problem in that area.

What I am having to struggle with is when I am in the user account and I click on the "Run as different user" link, I choose root and enter the root passwd. Afterward, I choose some apps to open, such as nautilus, vmware, and other. Nothing happens. The "Run as different user" just closes. I have to note that gedit and some other programs can be open via "Run as different user".

Am I missing something?

---

### Post by daddario on 2005-11-05
you can only login as root from the terminal!
now: STOP ASKING QUESTIONS IN THIST THREAD! IT'S NOT NICE!

---

### Post by domino on 2005-11-05
[QUOTE=daddario]you can only login as root from the terminal!
now: STOP ASKING QUESTIONS IN THIST THREAD! IT'S NOT NICE![/QUOTE]
Did something crawl up your ssa? That is about the stupidest answer I have ever come up on.

---

### Post by Ampersand on 2005-11-05
daddario: Have you tried this guide for installing Wine? [http://doc.gwos.org/index.php/Wine](http://doc.gwos.org/index.php/Wine)

domino: It tends to be better to start a new thread if you have a question, rather than asking in a thread that still has unresolved problems.

---

### Post by NewWithoutClue on 2005-11-05
To enable root to login either a) edit '/etc/gdm/gdm.conf' or b) run 'gdmsetup'
the options you wish to change are in there.
i also allowed root from within pams config file:
'/etc/pam.d/login' read the comments.

Note: the people are not being @55holes by telling you you shouldn't login as root; your computer will not deny root anything! root owns. and so does the programs running as root.

w00t,
Paul.

---

### Post by domino on 2005-11-05
> domino: It tends to be better to start a new thread if you have a question, rather than asking in a thread that still has unresolved problems.
That's fine. Then please explain to me how he got from "can not log in as root" to "installing wine"? I'm not trying to be a smartass of any sort. I'm just stating the obviouse.

**Enable root user**

sudo passwd root
su

**Gnome Display Manager**

In security tab, tick "allow root to log in with DGM". Log out user UI and log in as root. Now you can break your Breezy Badger install any way you like.

As for my question, I have already posted on the prior page. I personally don't  know why I should start a new thread since the topic of this thread suites my needs. Anyway, if answered or not, it doesn't matter anymore. I can only assume that the functionality is broke, or I am using the function the wrong way. Either or, tihs happens.

regards.

---

### Post by daddario on 2005-11-06
wine installed, I dont know why it didnt work on another computer (but I did the thing in synaptic). 

[quote=domino]Then please explain to me how he got from "can not log in as root" to "installing wine"? I'm not trying to be a smartass of any sort. I'm just stating the obviouse.[/quote]
both broblems were mine?

[quote=ampersand]Have you tried this guide for installing Wine? [http://doc.gwos.org/index.php/Wine](http://doc.gwos.org/index.php/Wine)[/quote]
yes I found something like thath, But I cant find something like thath four audacity.I quess I have to do in synaptic again?

I have never bin in a foreign forum before, so I dont know, is it normal to ask your questions in other peapoles threads, if it is im sorry for [quote=daddario]you can only login as root from the terminal!
now: STOP ASKING QUESTIONS IN THIST THREAD! IT'S NOT NICE![/quote>

---

### Post by daddario on 2005-11-07
Still, how can I do, thath, if ubuntu boots ub the x will not start untill I type: startx ?

---

