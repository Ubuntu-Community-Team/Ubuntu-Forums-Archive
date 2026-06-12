---
title: "Updates Not Working - Blocked Out!"
date: 2009-04-10
forum: General Help
---

### Post by Mel Shepherd on 2009-04-10
Please help me! I'm not new to Linux Unbuntu, but I consider myself very much a "newbie"because I do not have the basics down, such as how to load programs & how to make typed commands work.

Here is my problem. I have followed the advice of those who are helping others solve this dpkg problem that's seems to be pretty consistent among ubuntu distro users, but such advice is not helping me.  Here is the error message: [COLOR="Red"]**"E: dpkg was interrupted and you must manually run dpkg --configure -a" **[/COLOR] This command does nothing for me! It only brings me into where I am to type my password. However, I'm unable to type anything from this point on within the terminal. I'm about ready to delete Unbuntu and go back to windows, but this would be I feel a mistake because I would really like to find out how Linux works. What's the next problem that's going to cause me to give me? 

All this good and helpful advice give from the forum so far has come up empty for me. So, I decided to join the forum, even though I'm not all that much of a contributor. Remember, I'm a "Newbie" with my Unbuntu 8.10 distro install.  However, these are the facts as of 4/10/2009 - I cannot use Add & Remove, nor the Synaptic Package Manager, which I understand are better than this dpkg. Last night I spend several hours looking for help form the internet within my distro. Meaning,this distro is installed on VMWare Workstation 6.5, as a virtual machine. Every time I seek to install VMWare Tools using the instruction from the internet, it doesn't work. 

So, what do I do? Reinstall? The internet works fine. So, could anyone help me solve this "epkg problem" that others are having, but somehow have found help getting their updates?

---

### Post by irfan9727 on 2009-04-10
what do you mean by, typing anything won't work?
if you enter the password, then nothing shown after "[SUDO] password for <username> :", that's the way it is. Anything you type wouldn't shown. Just type the password like normal, then press enter.

If the system hungs, sorry, I'm also just a newbie :)

---

### Post by coffeecat on 2009-04-10
> **Mel Shepherd said:**
>  Here is the error message: [COLOR=Red]**"E: dpkg was interrupted and you must manually run dpkg --configure -a" **[/COLOR] This command does nothing for me! It only brings me into where I am to type my password. However, I'm unable to type anything from this point on within the terminal.

You need to type:

```
sudo dpkg --configure -a
```which I believe is what you are doing, since it asks you for your password. When you type in your password it is not echoed to the screen, which is why you think you are unable to type anything. This is a security feature, but does baffle a lot of newcomers.

---

### Post by Mel Shepherd on 2009-04-10
This command I have performed several times, but it doesn't work! While I'm typing this in this thread will take you through the process. First, I have pressed Alt & F2 so as to get to the "run the application window." I type "sudo dpkg --configure -a" to be run in the terminal. When I run with file nothing happens through this procedure either. I am brought into my home file, but I don't know what I am doing. Those things I try to do result in "no such file found." So, I click on run in the terminal. This brings me to (sudo password for mel72. When I try and type in this terminal window the keyboard doesn't work.

---

### Post by coffeecat on 2009-04-10
I really don't know why it doesn't work with the terminal from Alt-F2. I never use that. Go to Applications > Accessories > Terminal and try the command in that. That's a proper terminal.

---

### Post by Mel Shepherd on 2009-04-10
This I have done this as well, but it still doesn't work. I have tried Add & Remove, but can't remove what I think is the problem either. Unbuntu is free, but in some ways difficult to operate if you are a newbie.  

It's as if someone knows what I need to type and will not let me type that command. If I don't get any other reponse in by the end of the day, I believe I will delete the distro and start over again. This time, I will not use the automatic updates so easily. Just because their are updates is no sign they will work.

---

### Post by coffeecat on 2009-04-10
I'm sorry you are having problems. Yes, a new OS can be bewildering at first. It took me several months before I was really comfortable with Linux, but now I haven't booted into Windows for - well - months. I can still remember that epiphany moment when I realised I could do without Windows. It was a good feeling.

Anyway, I don't know what went wrong with your updates but, please believe me, problems are unusual with the updater. I have been regularly running each version of Ubuntu since late 2005, and I have only ever had minor problems with updates - usually when the update server was down - and never a problem which was as intractable as yours.

I wish you well.

---

### Post by iponeverything on 2009-04-10
Hi Mel - welcome to the forums. 

post the output of:

```
sudo tail -v /var/log/dpkg.log /var/log/messages /var/log/dmesg
```

---

### Post by Mel Shepherd on 2009-04-10
This brings me to (sudo password for mel72. And I can't do anything else.

---

### Post by zika on 2009-04-10
> **Mel Shepherd said:**
> This brings me to (sudo password for mel72. And I can't do anything else.
You will not see anything happening while You are entering the password. when finished with typing the password press "Enter". I hope that is the problem, if it is not please do not be angry with me, I was not trying to be smart ... :)

---

### Post by iponeverything on 2009-04-10
sudo will prompt for your password (you won't see it when you type it in) -- You then hit enter.

---

### Post by kpatz on 2009-04-10
```
kpatz@jaunty-beta:~$ sudo dpkg --configure -a
[sudo] password for kpatz:  (you type your password but it won't show up.  Press Enter afterward)
(results of dpkg command will appear here after you've typed your password and hit enter)

```

The password doesn't appear when you type it, so that someone watching you won't be able to read your password off the screen. ;)

Once you hit Enter, you should see something happen.

---

### Post by Mel Shepherd on 2009-04-10
It's not a matter of not typing the wrong command, but the fact I cannot type anything. I am locked out of using the terminal from that point on. This next week I believe I will delete the distro and think about whether I want to try Unbuntu again.  

Linux has problems just like Windows, but at least with Windows I understand what needs to be done to fix the problem.

---

### Post by _khAttAm_ on 2009-04-10
> **Mel Shepherd said:**
> 
Linux has problems just like Windows, but at least with Windows I understand what needs to be done to fix the problem.
what if you press enter?

Please describe your problem in good detail to have a solution.

---

### Post by genis200 on 2009-04-10
Please tell me, can you type anything in Terminal? Try this command.
```
dpkg --configure -a
```
Tell me about your problem and I'll be happy to help you any way possible.

---

### Post by Fourgun on 2009-04-11
I have the same problem as Mel.. that is I have the same error message.
when I type in " dpkg --configure -a " then enter password

This is what comes into the window, which makes no sense.

julie@julie-desktop:~$chanCe!
bash:chanCe!:command not found
julie@julie-desktop:~$

Why does this not make sense to me?
julie is my log in name
chanCe! is my password

I was at a forum and wrote a command in the terminal to download "extras"
like java and mp3 encoders and window pops up with download progess bar and then I go get coffee and when I come back it looks like a java agree to these terms page put I couldn't seem to do anything so I closed the window.

Then error message and can't use synaptic package manager.

Yes, I'm a neewbie to Ubuntu

---

### Post by coffeecat on 2009-04-11
> **Fourgun said:**
> I have the same problem as Mel.. that is I have the same error message.
when I type in " dpkg --configure -a " then enter password

This is what comes into the window, which makes no sense.

julie@julie-desktop:~$******
bash:chanCe!:command not found
julie@julie-desktop:~$

Why does this not make sense to me?
julie is my log in name
****** is my password

Welcome to the forum. I'll describe this step by step. Your password shouldn't appear on screen, so maybe you've made a simple error.

OK. Open a terminal. Type in:

```
sudo dpkg --configure -a
```and then press the Return key. You will now be prompted for your password. Type it in BUT IT WILL NOT APPEAR ON SCREEN. This is a security measure. At the end of your password, press return and you should see some terminal output as dpkg does its stuff.

Two points:

You may want to edit your post to remove your password. I've changed you password to ****** where I've quoted you.

You use the command 'sudo' in the terminal before any commands needing administrator rights, which dpkg does. And, yes I agree that it's a pity the error message doesn't tell you this. Experienced users know this; new users are simply perplexed.

Good luck.

---

### Post by Mel Shepherd on 2009-04-11
Okay, all is right! The information of the password "will not be shown" was the key thing I needed to know. I feel so dumb!! However, how do I change the password that I've reviewed in this forum? I realize I should not have shared my password, but how do I edit my comments after they've been posted? I'm looking in Forum Help and so far I haven't found that information. I tell you I'm a genuine newbie.

---

### Post by coffeecat on 2009-04-12
> **Mel Shepherd said:**
> how do I edit my comments after they've been posted?

Look at the bottom right of the post you want to edit. There are two buttons, quote and edit. Click on the edit button and your post comes up in editable format which you can then modify. A 'last edited by..' message will appear at the foot of your post. See my previous post - I was probably correcting a typo but didn't bother to give a reason.

If by chance you want to change your Ubuntu login password, go to System > Adminstration > Users and Groups, click on Unlock, highlight your account and click on Properties. That's for Ubuntu gnome. I can't remember whether you're using Ubuntu or one of the *buntu variants. If you're using Kubuntu or Xubuntu, there will be a similar utility but I can't remember where it would be.

---

### Post by Mel Shepherd on 2009-04-12
Please, I"m sorry my resolution is so small at 1900 x 1080 on a 32 inch screen that could hardly read those two words.  On my computer they are a blur. When I try to load package files it just stalls and goes no where, but maybe it's taking a long time to search for those updates. However, it did the same thing last night when I finally figured out what you were saying in your post. 

What do I do next? It says downloading packages, but the progress line isn't moving? I am forcing them to close !! 
I think something is wrong with my down loader.

Update: 4/12/2009 As of Easter Morning I tried doing the "sudo -configure -a" again and this is the message I am receiving ---------------- sudo: please use single character options
usage: sudo -h | -K | -k | -L | -l | -V | -v
usage: sudo [-bEHPS] [-p prompt] [-u username|#uid] [VAR=value]
            {-i | -s | <command>}
usage: sudo -e [-S] [-p prompt] [-u username|#uid] file ...

I also tried installing updates through updates through synpatic manager and it says I have another program in operation, but I'm shut everything down. What do I do next?

---

### Post by coffeecat on 2009-04-12
> **Mel Shepherd said:**
> my resolution is so small at 1900 x 1080 on a 32 inch screen that could hardly read those two words. 

You can change the default zoom setting in Firefox in the View menu. Also, you can change your desktop and application font sizes in System > Preferences > Appearance. 

> **Mel Shepherd said:**
> What do I do next? It says downloading packages, but the progress line isn't moving? I am forcing them to close !! 
I think something is wrong with my down loader.

Are you posting these posts from the same Linux installation or from Windows? Because this sounds like an internet connection problem. If this was so, and you left it, after a time you would get a failure to connect to server error.

To be honest, you might be better opening a new thread. This one's getting a bit long and moving on from the original problem.

---

### Post by 3rdalbum on 2009-04-12
For future reference (or maybe this will help you right now): When you get the license terms for Java, you need to press the Tab key to move the highlight to the "Agree" button. This instruction is regrettably not included anywhere in that window.

This appears to have been the reason why the package manager thought that configuring the Java package failed - you didn't know about pressing tab when you got the license agreement on the screen, and just closed the window.

---

