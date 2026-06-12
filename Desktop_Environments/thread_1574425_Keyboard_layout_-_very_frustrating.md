---
title: "Keyboard layout - very frustrating"
date: 2010-09-14
forum: Desktop Environments
---

### Post by Sciezyna on 2010-09-14
I am new to Linux. Installed the Ubuntu 10.04 Lucid (Gnome desktop). During the install I selected USA keyboard as default to avoid any 'funny' system installation problems.


I am searching for solved problem regarding USA keyboard forcing itself even though I:

Installed Polish layout - works.
Swapped Alt-L with Alt-R (System/Preferences/Keyboard)
Made Polish layout default (System/Preferences/Keyboard)
Removed the USA keyboard (System/Preferences/Keyboard)

The USA keyboard comes back as the default regardless. I do not need the USA keyboard as default I need the Pl keyboard. Is this a hint that anything American must be better? ;)

Additionally the Gnome desktop panel crashes from time to time but I am used to things like that because I used MS-DOS and Windows for the last ~20 years... 

It is now second week of searching and well over a hundred searches all over the Internet, Linux and Ubuntu forums. It seems there is nobody who actually knows or gives two hoots. The only listings I found are hundreds of users with the same problem - not solved.

Yes I am irritated because I heard so many prizes of Linux and its superiority over Windows. I am still convinced that Linux is a good choice for me, however...

As I see it, (maybe I am a moron) a keyboard is a basic input tool for any computer - basic (including mobiles, washing machines, Air Conditioners, CALCULATORS and a light switch, and more).

Is here anybody looking through here, from the Linux development team and reading any of this? DO they care? Don't they have 'agents to do it?

The only thing I got VERY CLEARLY from the multitude of post by 'very experienced users' I read here is "Don't mess with the 'root' account" OK I will not!

Yes I can keep hitting the 'Kb' switch applet on the panel if someone tells me that "nobody knows how to fix the problem and that is the way".

I would be satisfied if somebody knowledgeable informed me that: Yes we know about this problem - even though some posts are dated 2005.

My idea is that the USA keyboard will be coming back because I used it during the installation. I would not like to do fresh install from scratch because it would remind me of MS Windows. But if this is the only solution please tell me and I will make farther decision what to do, however, I would not be any more so kin as to irresponsibly advertise Linux as an OS superior over Windows.

Please help!

---

### Post by 3Miro on 2010-09-14
Can you just install the Polish layout, make it default and leave the US one in there. Uncheck "separate layouts for each window" and this should leave only the Polish layout active, even if the US one is present in the options menu.

I use two layouts, US and Bulgarian, since Bulgarian one is in Cyrillic, I cannot use my computer without the US keys (URL, terminal commands and so on are all in English). The US layout might be in there for such compatibility reasons.

---

### Post by Sciezyna on 2010-09-14
Thank you for quick replay.

I do not worry about the USA kb being there as an option.

I did select the Polish keyboard as the default (top of the lost), ticked off the 'Separate layouts for each window' and made the changes "Apply-System Wide'.

The thing is that every logout/login my keyboard still defaults to USA...

What irritates me is that all those selections and settings are simply not working. In session I have the 'Pol' indicator in the panel. Logout/Login USA is lit in the panel and of course I do not have the special Polish characters.

Thanks again 3Miro.

---

### Post by 3Miro on 2010-09-14
I cannot test with Ubuntu right now, since I am at work and I only have Arch Linux here, however, when I select "Bulgarian" as default (top of the list) in the Keyboard Layout settings then log out and then back in, I do get Bulgarian as the default. This means that the problem is not general for Gnome.

Your system has one component that mine doesn't right now. You are using GDM, which is responsible for the login screen when you type your username and password. GDM does use Keyboard Layouts, when I use Ubuntu, I sometimes get to the login screen, try to type a password and and it rejects me. Then I try again and again and at the end it turns out that I have been using the wrong layout the entire time. Here is my advice, try changing the keyboard layout on the login screen (there should be an option at the bottom). If this doesn't work, I will see what I can do tonight, when I get back to my Ubuntu machine.

---

### Post by Sciezyna on 2010-09-14
This is very kind of you to take interest in my problem.

I just tried your suggestion but at the login screen I do not have the language options... All I have is a window (ubuntu and logo) with three options to login:

Juliusz
Sarah
other
(cancel)   (Log in)

I do have two accounts.

Thanks
J

---

### Post by 3Miro on 2010-09-14
You should have something that looks like this picture:

[http://www.google.com/imgres?imgurl=http://www.debianadmin.com/wp-content/gallery/1004/1.png&imgrefurl=http://www.debianadmin.com/ubuntu-10-04-lucid-alpha-3-screenshots-gallery-updated-with-new-wallpapertheme.html&usg=__YYFcT_tBu_WXLr2XLjhCZ24mj4Y=&h=600&w=800&sz=236&hl=en&start=20&sig2=GEjHXjgSF0ZRkC8p_NfiqQ&zoom=1&tbnid=KPVaBGMNi_6bAM:&tbnh=142&tbnw=188&ei=ypyPTIuBHYG88gav3LyRDg&prev=/images%3Fq%3Dubuntu%2Blogin%2Bscreen%2B10.04%26um%3D1%26hl%3Den%26sa%3DN%26biw%3D1237%26bih%3D743%26tbs%3Disch:10,636&um=1&itbs=1&iact=rc&oei=uZyPTKqjLsPAswbNud3JCw&esq=2&page=2&ndsp=24&ved=1t:429,r:0,s:20&tx=111&ty=49&biw=1237&bih=743](http://www.google.com/imgres?imgurl=http://www.debianadmin.com/wp-content/gallery/1004/1.png&imgrefurl=http://www.debianadmin.com/ubuntu-10-04-lucid-alpha-3-screenshots-gallery-updated-with-new-wallpapertheme.html&usg=__YYFcT_tBu_WXLr2XLjhCZ24mj4Y=&h=600&w=800&sz=236&hl=en&start=20&sig2=GEjHXjgSF0ZRkC8p_NfiqQ&zoom=1&tbnid=KPVaBGMNi_6bAM:&tbnh=142&tbnw=188&ei=ypyPTIuBHYG88gav3LyRDg&prev=/images%3Fq%3Dubuntu%2Blogin%2Bscreen%2B10.04%26um%3D1%26hl%3Den%26sa%3DN%26biw%3D1237%26bih%3D743%26tbs%3Disch:10,636&um=1&itbs=1&iact=rc&oei=uZyPTKqjLsPAswbNud3JCw&esq=2&page=2&ndsp=24&ved=1t:429,r:0,s:20&tx=111&ty=49&biw=1237&bih=743)

Checkout the Keyboard Setting at the bottom, for this person it is set to "United Kingdom". This maybe only becoming active when you select a user and start typing a password.

---

### Post by Sciezyna on 2010-09-14
Well,

I did not have the bottom panel at the login window.

Just before you have sent your replay I did update/upgrade my OS with apt-get update and apt-get upgrade. It took a while...

I read your message and did what you suggested and IT WORKS!!! The panel is there and there are many options. Selected the Pol kb and is SOLVED.

Thank you very much 3Miro. Thank you. :D

Juliusz

---

### Post by 3Miro on 2010-09-14
Hopefully the update also fixed the crashing panel bug.

Enjoy Ubuntu :D

---

### Post by Sciezyna on 2010-09-14
I will observe the panel and write about. I think to post new Thread with hm.. different title and the link to the solution with your replays.

That was very nice.

Bulgarian... Polish... the world is rather small nowadays.

Regards
Juliusz

---

