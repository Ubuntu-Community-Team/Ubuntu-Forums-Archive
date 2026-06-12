---
title: "System menus are shown with square characters"
date: 2008-09-01
forum: Desktop Environments
---

### Post by n00bubunter on 2008-09-01
Hi everyone, my name is Elias and i'm really new to ubuntu. Since last week i'm having this error that is driving me insane. I think it's due to a problem with gnome. Magically (I really don't think it has been magically) ubuntu desktop enviroment stopped showing normal fonts and begun showing squared characters. Firstly i thought it could be a language problem, i mean someone accidently changed the default language to chinese. So i tried to change language, something quiet impossible because i don't know what i'm selecting due to the square characters. So i selected a random language and ubuntu tried to download some packages and before ending it threw an error. Of course i don't know what error. Then i tried to go to the PC explorer and it threw error. Every system task i want to open it keeps on giving me errors. Luckyly if I open a terminal, although the GUI shows the square characters the command line looks ok. The same happens with firefox (if not I wouldn't be able to write this kilometric thread :-D). So that's why I assume it's a GUI problem and therefore a Gnome problem. I made an apt-get upgrade and when it finished downloading all the packages an error came out. I wanted to upgrade or reinstall Gnome and more problems came out:
1) I don't know how to do it 
2) I don't want to break it more

So really I feel like i'm naked in the middle of the city while everyone is watching me saying Ha - Ha (with nelson's voice) not knowing where to go. I think the machine is screwd up and that i'm going to have to format it but I would like it to be the last option, there is a lot of information I cannot loose. 

Thanks in advance to anyone who reads this boring thread

P.S.: Excuse me for my bad english, i'm from argentina :P

---

### Post by n00bubunter on 2008-09-01
Sorry i forgot to attach these 2 screenshots so that you can see what the problem is. The second screen shows that the terminal looks good but the GUI doesn't.

[[IMG]http://img48.imageshack.us/img48/9766/screenshotml0.th.png[/IMG]](http://img48.imageshack.us/my.php?image=screenshotml0.png)

[[IMG]http://img76.imageshack.us/img76/2167/screenshot1ye7.th.png[/IMG]](http://img76.imageshack.us/my.php?image=screenshot1ye7.png)

---

### Post by knattlhuber on 2008-09-01
Please post the output of

```
cat /var/lib/locales/supported.d/local
cat /etc/environment
```

---

### Post by n00bubunter on 2008-09-01
> **knattlhuber said:**
> Please post the output of

```
cat /var/lib/locales/supported.d/local
cat /etc/environment
```

thanks for the quick answer. The output of 
 
```
cat /var/lib/locales/supported.d/local
```

is 

```
en_AU.UTF-8 UTF-8
en_US.UTF-8 UTF-8

```

and the output of 

```
cat /etc/environment
```

is

```
PATH="/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/bin/X11:/usr/games:/usr/lib/java/bin"
LANG="en_BW.UTF-8"
LANGUAGE="en_BW:en"
```

---

### Post by knattlhuber on 2008-09-01
Ugh. I had 'hoped' for some obvious error in the locale settings but they seem to be alright (Australian, US and Botswana English).

You could try

```
export LANG="en_AU.UTF-8"
export LANGUAGE="en_AU:en"
```

to set your environmental language variables to match your locale but I'm not sure if that'll fix your problem.

Have you tried navigating to System > Prefs > Appearance (Fonts tab) and change the application font?

I'm really at a loss here. You could reinstall the ubuntu-desktop

```
sudo apt-get install ubuntu-desktop
```

but again, I'm not sure if that'll help. Sorry.

Maybe someone else has a suggestion?

---

### Post by n00bubunter on 2008-09-01
hi knattlhuber thanks for your reply. I tried the export command but nothing seems to happen. I can't navigate to  System > Prefs > Appearance (Fonts tab) because i don't know where it is (square fonts :P). Perhaps reinstalling the ubuntu-desktop might work but I don't know if it will come up with compatibility issues or with data loss. I'm also lost here. Reinstalling or formatting should be the last resource because i don't have another disk to make backups. 

I forgot to say that this PC has Ubuntu 6.06 installed and it has eclipse installed with some projects. Perhaps there is some configuration mistake, but as I'm not used to give ubuntu support  i'm  really guessing here.

---

### Post by n00bubunter on 2008-09-01
Hi again. I navigated to the language selection item (I think, is the one that has the US and the German flag as an icon) and it gave me a message box. This message box let me copy the message and paste it in open office word. The message said:

```
The language support is not installed completely

Not all translations or writing aids, that are available for the supported languages on your system, are installed.
```

and below that says:

```
language-pack-kde-en (120k)
language-pack-kde-en-base (3036k)
```

it says KDE, I thought that I was using Gnome. Perhaps someone switched Gnome to KDE, how can I find out wich desktop enviroment I'm using?. I should do it via the command line. I'm going to search how to do it. I'll let you know if anything else comes up. 

Thanks again to anyone that is reading this.

---

### Post by knattlhuber on 2008-09-01
> **n00bubunter said:**
> Hi again. I navigated to the language selection item (I think, is the one that has the US and the German flag as an icon) and it gave me a message box. This message box let me copy the message and paste it in open office word. The message said:

```
The language support is not installed completely

Not all translations or writing aids, that are available for the supported languages on your system, are installed.
```

and below that says:

```
language-pack-kde-en (120k)
language-pack-kde-en-base (3036k)
```

it says KDE, I thought that I was using Gnome. Perhaps someone switched Gnome to KDE, how can I find out wich desktop enviroment I'm using?. I should do it via the command line. I'm going to search how to do it. I'll let you know if anything else comes up. 

Thanks again to anyone that is reading this.

You are using Gnome judged from your screenshots.
I get actually the same message (including the KDE stuff) on my copy of Hardy so that is definitely not related to your problem.

---

### Post by overdrank on 2008-09-01
I am going to pop in here and make a quick statement after conversing with the op. If this issue is a joke then end it now, do not waste the time and effort of those trying to help. :rolleyes:

---

### Post by n00bubunter on 2008-09-01
Well we already chat with overdrank via PM and I already told him this is not a joke. I'm not willing to waste others time. Simply I can't come up with the solution of this problem and I really need help. I'm sorry if it seemed to be a joke.

---

### Post by overdrank on 2008-09-01
Hi and the error says they are not completely installed, this is just a shot in the dark but you may try the commands ```
sudo apt-get install -f
sudo dpkg --configure -a

```

---

### Post by n00bubunter on 2008-09-01
Nope it didn't work :-(. I've been reading that Gnome uses configuration files for each user. So if a user has a problem perhaps another one or a new one doesn't have it. Here the problem seems to be more complex. When Ubuntu is booting everything seems fine, the fonts are ok. But when I get to the login screen I get those awful square characters. Perhaps the problem is in another place. I'll keep on searching.


----More News----
While I was writing this post I was dealing with the problematic machine. This time i could copy the error message that pops up when i try to open the PC explorer. It says

```
The Application "nautilus" has quit unexpectedly. 
You can inform the developers of what happende to hel them fix it. Or you can restart the application right now.
```

I'm thinking that this machine has become too buggy to get it solved. Perhaps the only way to solve the problem is to reinstall ubuntu.

---

### Post by bscook on 2008-09-11
n00bubunter:  

Were you able to solve this problem?  I just tried upgrading to 8.04 today and i appear to have lost all my fonts.  all that renders are a bunch of squares where i expect to see a font.  terminal access is okay; how did you solve this?

thx

---

### Post by pmcclure on 2008-09-15
Did anybody solve this? - I spent 3 days upgrading and installing new software and added VMware (that was a day) and all of sudden after a reboot i can only use shell

---

### Post by Giant Speck on 2008-09-15
I'm just throwing this out there, but perhaps it's trying to display a font that doesn't exist?  Have you tried changing the fonts?  I wonder if you can change them from within the terminal...

---

### Post by dagdo on 2009-01-08
I think its permission problems.

please "cd /usr/share/fonts"
and "sudo chmod a+r *.ttf"

cheers!

---

### Post by magicfab on 2009-04-15
@Dagdo, thanks, that fixed it for a friend in Jaunty.

Cheers,

Fabian

---

### Post by tamas305 on 2009-04-15
I had this problem also when the package manager was working and it encountered an error while downloading. All text was replaced with the same squares that he has. This is not a great solution but if nothing but nuking and paving remains than try this.

Hold down the power button and restart Ubuntu. Expect the Ubuntu splash screen to show up. After that the blinking cursor will appear in the top left where it usually does but depending on the speed of your system it should stay there for quite a while. However, instead rebooting wait and let Ubuntu think it though and if your lucky, like I was, the login screen showed up after 10 minutes. When I logged in, the two panels (top and bottom) did not show for a while but they came back and all the text was magically fixed. I am relatively new to Ubuntu so I do not know why this worked but if no one offers a better solution, give it a whirl.

-tamas

---

### Post by jaenmedina on 2009-10-30
OK. Go to etc/share/fonts. If the folder is empty then you need to install some fonts. You can download some from: 

     [http://sourceforge.net/projects/dejavu/files/dejavu/dejavu-fonts-ttf-2.30.tar.bz2](http://sourceforge.net/projects/dejavu/files/dejavu/dejavu-fonts-ttf-2.30.tar.bz2)

After you download that ishue:

     tar -xvf dejavu-fonts-ttf-2.30.tar.bz2

Go inside the folder you just untarred, then go into a folder named "ttf"
Inside that folder issue the following commands:
     
     install -v -d -m755 /usr/share/fonts/dejavu 
     install -v -m644 *.ttf /usr/share/fonts/dejavu
     fc-cache -v /usr/share/fonts/dejavu

After that, reboot your desktop and let me know how it went.
Hope this helps.

---

### Post by robwa2 on 2009-12-18
I have the same problem!

I actually post it in **Instalation and Upgrades** but nobody helps me :( 

This is the post

*I've been trying to install opencv in ubuntu 7.10 with no internet connexion, what I've been doing is downloading all the -dev packages that the installation process has been asking for and using synaptic manager to install the packages as well..anyway, I was installing packages related to xorg and after that I installed** libxkbui1_1.0.0-2_i386.deb** all the fonts in synaptic manager turn into squares!!!! .. How can I solve this? Please HElp!*
[SIZE=2]
[SIZE=1]After that, someone told me to uninstall the package so I did sudo dpkg -r libxkbui1 and restarted the PC and now and I CAN'T SEE ANY FONT in desktop or [/SIZE][/SIZE][SIZE=1]system menus.

I already did the sudo chmod a+r *.ttf[/SIZE] and restarted the terminal, but should I restart the computer as well?? .. If this doesn't work what can I do?

---

### Post by robwa2 on 2009-12-19
Problem solved! .. I reinstalled libxkbui, libxkbui-dev and libxkbu1 .. after that I reinstalled Pango and everything came to normal :)

---

