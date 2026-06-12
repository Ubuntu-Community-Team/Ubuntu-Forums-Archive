---
title: "Icons for nautilus (root)..."
date: 2005-12-10
forum: Desktop Environments
---

### Post by okt on 2005-12-10
Well I am a pretty new user to Linux in general, but have use the Ubuntu Live CD's for a while. Well Windows XP crapped out on me so I said enough with this unreliable crap and moved to the wonderful and beautiful world of Linux. I am running Ubuntu 5.10, with Gnome, and I came across some nice skins and icon themes that I would like to use. I installed them and applied them and everything looks great until...

~$ sudo nautilus

I do this or try to run any folder with root abilities from my account and all the icons are a generic piece of paper. I get the theme to apply to it by changing a file to use my theme as the default theme for that. The icons though...

If there is another thread explaining this just link me, I did search however for a good 20 or so minutes, but forgive me if I over saw something.

Thanks, 
an overjoyed Linux noob.

---

### Post by aysiu on 2005-12-10
Have you tried this? ```
gksudo gnome-theme-manager
```

---

### Post by arnieboy on 2005-12-10
[QUOTE=okt]Well I am a pretty new user to Linux in general, but have use the Ubuntu Live CD's for a while. Well Windows XP crapped out on me so I said enough with this unreliable crap and moved to the wonderful and beautiful world of Linux. I am running Ubuntu 5.10, with Gnome, and I came across some nice skins and icon themes that I would like to use. I installed them and applied them and everything looks great until...

~$ sudo nautilus

I do this or try to run any folder with root abilities from my account and all the icons are a generic piece of paper. I get the theme to apply to it by changing a file to use my theme as the default theme for that. The icons though...

If there is another thread explaining this just link me, I did search however for a good 20 or so minutes, but forgive me if I over saw something.

Thanks, 
an overjoyed Linux noob.[/QUOTE]
thats because when u run nautilus as root (with sudo), the themes that u applied wont work since they werent applied as root user.

---

### Post by arnieboy on 2005-12-10
yes run the theme manager with sudo as aysiu said
```
sudo gnome-theme-manager 
```
and then apply the nautilus for the root user.

---

### Post by okt on 2005-12-10
Thanks both of you... I am having trouble installing the icon theme running it this way. Is there a manual way to install them? Also is there an actual root account?

EDIT: Also without making another topic somewhere... I am looking for information on where I can get *drivers* for my ATi Radeon X850XT.

---

### Post by aysiu on 2005-12-10
[QUOTE=okt]Thanks both of you... I am having trouble installing the icon theme running it this way.[/quote] Specifically what trouble do you encounter? 

> Is there a manual way to install them? Yeah. Drag and drop the icon theme .tar.gz into the theme manager window. 

> Also is there an actual root account? Not unless you create it.

---

### Post by okt on 2005-12-10
[QUOTE=aysiu]
 Yeah. Drag and drop the icon theme .tar.gz into the theme manager window. 
[/QUOTE]

All I get is an "Installation Failed" error popup.

I have tried to redownload the theme aswell...:confused:

EDIT: Strange thing is when I try to redownload it it doesn't seem to even take any time, like it is already downloaded...

---

### Post by arnieboy on 2005-12-10
root is ALWAYS there in any unix based system. It is never disabled or removed.
In the case of ubuntu root has a randomly generated password which can be reset by:
```
sudo passwd root
```

it is very important that misinformation is not spread among new users.. they are made to think that the root user does not exist at all in Ubuntu.. and its "disabled" by default.
Such misinformation needs to be dispelled because it leads to a lot of wrong concepts.

---

### Post by aysiu on 2005-12-10
[QUOTE=okt]All I get is an "Installation Failed" error popup.[/quote] Did that same theme work when you drag and dropped it for your user (not gksudo)?

---

### Post by aysiu on 2005-12-10
[QUOTE=arnieboy]root is ALWAYS there in any unix based system. It is never disabled or removed.
In the case of ubuntu root has a randomly generated password which can be reset by:
```
sudo passwd root
```[/QUOTE] I stand corrected. Thanks, arnieboy.

---

### Post by okt on 2005-12-10
[QUOTE=aysiu]Did that same theme work when you drag and dropped it for your user (not gksudo)?[/QUOTE]

Yes sir.


EDIT: arnieboy, thanks! I am learning so much!

---

### Post by aysiu on 2005-12-10
[QUOTE=okt]Yes sir.[/QUOTE] Can you put up a link to the icon theme, so I can do a little testing?

---

### Post by okt on 2005-12-10
[QUOTE=aysiu]Can you put up a link to the icon theme, so I can do a little testing?[/QUOTE]

Ofcourse,

**Dropline Etiquette**
[http://www.gnome-look.org/content/show.php?content=27399](http://www.gnome-look.org/content/show.php?content=27399)

---

### Post by arnieboy on 2005-12-10
The correct way to install icon themes in GNOME is as follows:
Download the icon theme in your home folder. lets say the name of the file is **mytheme.tar.gz**
do the following from  terminal
```
cd ~/.icons
tar xzf ~/mytheme.tar.gz
```
where u need to replace mytheme.tar.gz with the correct name of the theme.
now go to theme manager and select your icon theme.
that shd get u all set.

P.S.: most theme files are gunzipped files (have tar.gz extension)
if they are bzip files, u have to use the "j" switch instead of "z"
so thelast command would like:
```
tar xjf mytheme.tar.bz
```

---

### Post by aysiu on 2005-12-11
It worked for me.
That just makes your error even more of a mystery...

You're doing Alt-F2 and then typing ```
gksudo gnome-theme-manager
``` right?

---

### Post by okt on 2005-12-11
[QUOTE=arnieboy]The correct way to install icon themes in GNOME is as follows:
Download the icon theme in your home folder. lets say the name of the file is **mytheme.tar.gz**
do the following from  terminal
```
cd ~/.icons
tar xzf ~/mytheme.tar.gz
```
where u need to replace mytheme.tar.gz with the correct name of the theme.
now go to theme manager and select your icon theme.
that shd get u all set.

P.S.: most theme files are gunzipped files (have tar.gz extension)
if they are bzip files, u have to use the "j" switch instead of "z"
so thelast command would like:
```
tar xjf mytheme.tar.bz
```[/QUOTE]

Ok that sounds about right... what about a tar.bz**2** file?

---

### Post by arnieboy on 2005-12-11
same switch as bz
infact most modern bzipped files have the tar.bz2 extension

---

### Post by okt on 2005-12-11
[QUOTE=arnieboy]same switch as bz
infact most modern bzipped files have the tar.bz2 extension[/QUOTE]

Doesn't seem to be working for me... Maybe I am doing something extreamly noobish... :)
```
username@ubuntu:~/.icons$ tar xjf DroplineEtiquette.tar.bz2
tar: DroplineEtiquette.tar.bz2: Cannot open: No such file or directory
tar: Error is not recoverable: exiting now
tar: Child returned status 2
tar: Error exit delayed from previous errors

```

---

### Post by arnieboy on 2005-12-11
[QUOTE=okt]Doesn't seem to be working for me... Maybe I am doing something extreamly noobish... :)
```
username@ubuntu:~/.icons$ tar xjf DroplineEtiquette.tar.bz2
tar: DroplineEtiquette.tar.bz2: Cannot open: No such file or directory
tar: Error is not recoverable: exiting now
tar: Child returned status 2
tar: Error exit delayed from previous errors

```[/QUOTE]
yes what u are doing is giving it the wrong path. thats ok.. we all start learning someday.
what u need to do is the following:
tar xjf <path to>/DroplineEtiquette.tar.bz2
in this case <path to> would be your home folder if u have the file downloaded in your home folder. hence it wouldlook as follows:
```
cd ~/.icons
tar xjf ~/DroplineEtiquette.tar.bz2
```

"**~**" represents your home folder. u can also write it as **$HOME**. they mean the same.

---

### Post by okt on 2005-12-11
Ah thankyou! 
However the icons are still not showing up in the sudo run *gnome-theme-manager* so I am not sure how to install them to have access to them from the root.

---

### Post by aysiu on 2005-12-11
Please wait until Arnieboy confirms that this is safe to do, but I'd imagine you would do something like ```
sudo cp -r ~/.icons /root/.icons
```

---

### Post by okt on 2005-12-11
[QUOTE=aysiu]Please wait until Arnieboy confirms that this is safe to do, but I'd imagine you would do something like ```
sudo cp -r ~/.icons /root/.icons
```[/QUOTE]

Which if I have learnt anything is linking the root /.icons to my /.icons? Am I correct?

---

### Post by arnieboy on 2005-12-11
[QUOTE=okt]Ah thankyou! 
However the icons are still not showing up in the sudo run *gnome-theme-manager* so I am not sure how to install them to have access to them from the root.[/QUOTE]
they will not show up in theme manager when u run it as root (with sudo) for obvious reasons.
1) u installed the icons for your user account (not for root)

if u want it to show up when u run  itas root. u will need to do the following:
if u already havent set your root password, do
```
sudo passwd root
```
now do the following:
```
su
cd ~/.icons
tar xjf /home/**arnie**/DroplineEtiquette.tar.bz2
exit
exit
```
u will need to replace **arnie** with your **user name**
now run 
```
sudo gnome-theme-manager
```
and u will find the icon theme in your root theme manager

---

### Post by aysiu on 2005-12-11
[QUOTE=okt]Which if I have learnt anything is linking the root /.icons to my /.icons? Am I correct?[/QUOTE] Again... don't do this until Arnieboy or someone else chimes in that it's cool to do. I may have a high post count, but I'm still a newbie in many ways.

Theoretically, it's copying your entire .icons folder from your user account to the root account.

---

### Post by arpunk on 2005-12-11
No, *sudo cp -r ~/.icons /root/.icons* will copy them to /root/.icons/
For linking files and directories you can use the *ln* command. And for learning more about it you can do *man ln* in a terminal. Same goes with *cp* and all other console commands and programs.

---

### Post by okt on 2005-12-11
ok well thanks for the correction. 

It would appear that "root" doesn't have /.icons in the home dir. :confused:

---

### Post by arnieboy on 2005-12-11
[QUOTE=okt]ok well thanks for the correction. 

It would appear that "root" doesn't have /.icons in the home dir. :confused:[/QUOTE]
simply create a .icons directory in your root home directory.
```
su
mkdir ~/.icons
```

---

### Post by aysiu on 2005-12-11
[QUOTE=okt]
It would appear that "root" doesn't have /.icons in the home dir. :confused:[/QUOTE] .icons is a hidden directory. Are you using ```
gksudo nautilus
```? If so, press control-h.

---

### Post by arnieboy on 2005-12-11
[QUOTE=aysiu].icons is a hidden directory. Are you using ```
gksudo nautilus
```? If so, press control-h.[/QUOTE]
no. the .icons directory **might not be there** because this user has not logged into GNOME as root even once. most hidden directories in gnome (for any user account) get created once u log into gnome as that specific user for the first time.

---

### Post by aysiu on 2005-12-11
[QUOTE=arnieboy]no. the .icons directory **might not be there** because this user has not logged into GNOME as root even once. most hidden directories in gnome (for any user account) get created once u log into gnome as that specific user for the first time.[/QUOTE] Damn. Wrong again. Thanks for the correction. I think I may just shut up in this thread from now on.

---

### Post by okt on 2005-12-11
ok I think I may have messed things up earlier...

I get "This link can't be used, because its target "/root/.icons" doesn't exist."

---

### Post by okt on 2005-12-11
[QUOTE=aysiu]Damn. Wrong again. Thanks for the correction. I think I may just shut up in this thread from now on.[/QUOTE]

No need to do that! If you hadn't have said anything then I wouldn't have gotten the anwser! :p

---

### Post by arnieboy on 2005-12-11
[QUOTE=aysiu]Damn. Wrong again. Thanks for the correction. I think I may just shut up in this thread from now on.[/QUOTE]
no thats ok.... what I am really concerned about is the misinformation being spread among new ubunteros that using su (instead of sudo) is unsafe. 
sudo is a  lot more unsafe simply because, if i hack into your system with your user password, I can use your password and sudo to delete almost everything on your computer. To access su, I atleast need the root password which is different from the user password.

All this misinformation gets propagated and finally make people make all sorts of stupid claims about the root user and su.

Please do bear in mind though that **logging into GNOME as root** and using it like a normal user is **unsafe** because u are opening up your computer to potential hackers.

At the same time, making sudo too powerful in any distro is doing exactly the same thing. This is exactly the reason why use of sudo in discouraged is most other distros.

---

### Post by arnieboy on 2005-12-11
[QUOTE=okt]ok I think I may have messed things up earlier...

I get "This link can't be used, because its target "/root/.icons" doesn't exist."[/QUOTE]
yes thats exactly what i was talking about. hope u created the .icons directory and got everything up and working.

---

### Post by okt on 2005-12-11
[QUOTE=arnieboy]yes thats exactly what i was talking about. hope u created the .icons directory and got everything up and working.[/QUOTE]

Ok thing is is there is a 6kb .icons file/folder (BTW which is it) and it won't open I get the error listed above, and if I try to move it to the trash it does nothing. I can't rmdir  because rmdir: `/root/.icons': Not a directory.

---

### Post by arnieboy on 2005-12-11
alright do the following step-by-step (nothing more/nothing less)
```
su
rm -rf ~/.icons
mkdir ~/.icons
cd ~/.icons
tar xjf /home/arnie/DroplineEtiquette.tar.bz2
exit
exit
```
replace **arnie** with your user name.

---

### Post by okt on 2005-12-11
Perfect! Thanks so much for helping me along.

---

### Post by arnieboy on 2005-12-11
glad to be of help. enjoy ubuntu.

---

### Post by meborc on 2005-12-31
sorry to bump this thread, but i had the similar problem, and tried to adress it as described above...

BUT... i get as far as **gksudo gnome-theme-manager**, i have my desired icon theme, i select it, everything seems normal... i close the dialog and try **sudo nautilus**, and see that ugly root theme again :confused: 

so what i did was exactly what was said in this thread... and i installed the icon theme under the .icons in su... but it seems that my nautilus doesn't recognise that i have changed the theme...

i know it must be frustrating to deal with these new-ubuntu-user questions, but if you could help, arnieboy, i would be most grateful

---

### Post by Bou on 2005-12-31
I think linking all the content of .icons to /usr/share/icons should solve this whole issue. Same with .themes and /usr/share/themes. Just a guess, though, someone please give it a try.

Bye!

---

### Post by meborc on 2005-12-31
well i guess the problem is not there... cuz as i run **sudo gnome-theme-manager** i SEE the icon theme there... i chose it... i exit... and it soesn't work... what am i doing wrong? :(

---

### Post by piedamaro on 2005-12-31
I've always linked my ~/.icon folder under /root no problems so far, no update required no gnome-theme-manager, nothing. It just does the Right Thing.

P.S.: if you give the root nautilus a custom background color, you can differntiate it from a normal nautilus window, same goes for gedit, very useful! ;)

---

### Post by meborc on 2005-12-31
EDIT: ok, what i did was **sudo ln -s /home/kaspar/.icons /root/** and that did the trick... hope that helps anybody else... 

this should be in ubuntu by default... so that the icons are nice and pretty, but the background is one big red text: you are using root... you are using root... :) thanks everybody for helping me

---

