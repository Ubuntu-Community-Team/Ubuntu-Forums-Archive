---
title: "Upgrade KDE 4.5.1 to KDE 4.6?"
date: 2011-04-12
forum: Desktop Environments
---

### Post by galacticaboy on 2011-04-12
I am running Kubuntu 10.10 now. It comes with KDE 4.5.1, I would like to upgrade to 4.6. I do not care if it is stable or whatever, I just want to do it. I am sorry if I am sounding rude, but if you are just going to tell me to stick with 4.5.1, then please do not reply. I am tired of people telling me what to do. I just asked a question if you have an answer answer, if not don't. If I am going to make a mistake, let me make it! I learn from them that way! Thank you for understanding!
David

---

### Post by 3Miro on 2011-04-12
What's with the flames? Just use Google: "kde 4.6  ubuntu 10.10"

First hit:

[http://www.ubuntugeek.com/how-to-install-kde-4-6-in-ubuntu-10-10.html](http://www.ubuntugeek.com/how-to-install-kde-4-6-in-ubuntu-10-10.html)

You install an unofficial repo, then update from it and you have it. Enjoy!

---

### Post by SeijiSensei on 2011-04-12
Yes, you are being rude, but I'll ignore it this one time.  

You need to add the backports repository to KPackageKit.  Open KPackageKit and click the Edit Origins button.  Choose the "Other Software" tab, then click the Add button and enter "ppa:kubuntu-ppa/backports".  That will add the repository and key.  Update your sources when prompted.  Then choose Software Updates from the main KPackageKit menu, and it should find a whole bunch of new KDE packages that are from 4.6.2.

Sometimes people come here and ask to do something that might cause them problems.  It's not unreasonable to say "don't do that" in that case.

---

### Post by galacticaboy on 2011-04-12
> **SeijiSensei said:**
> Yes, you are being rude, but I'll ignore it this one time.  

You need to add the backports repository to KPackageKit.  Open KPackageKit and click the Edit Origins button.  Choose the "Other Software" tab, then click the Add button and enter "ppa:kubuntu-ppa/backports".  That will add the repository and key.  Update your sources when prompted.  Then choose Software Updates from the main KPackageKit menu, and it should find a whole bunch of new KDE packages that are from 4.6.2.

Sometimes people come here and ask to do something that might cause them problems.  It's not unreasonable to say "don't do that" in that case.

I understand if it would brake my system, but I have had people on here, well a lot, just post and tell me that I should not install it because it is ugly. I do not appreciate that, I will decide if it is ugly or not. If I offended anyone I am sorry that was not my intention. I just want an answer, not someone beating around the bush trying to get "Beans" because I beleive that it what people are sometimes trying to do by trolling and other crap on here. I love these forums, but when I want an answer, I want an answer, not a half *** answer. If you do not know, fine, I appreciate your time, if you do know the answer, great! You are my new friend as you helped me!

---

### Post by 3Miro on 2011-04-12
> **galacticaboy said:**
> I understand if it would brake my system, but I have had people on here, well a lot, just post and tell me that I should not install it because it is ugly. I do not appreciate that, I will decide if it is ugly or not. If I offended anyone I am sorry that was not my intention. I just want an answer, not someone beating around the bush trying to get "Beans" because I beleive that it what people are sometimes trying to do by trolling and other crap on here. I love these forums, but when I want an answer, I want an answer, not a half *** answer. If you do not know, fine, I appreciate your time, if you do know the answer, great! You are my new friend as you helped me!

If you see "trolling" or "abuse" then you can report it to the mods (there is a "report abuse" button next to every post).

What is not a good idea, is to make me read your rant, when I have never done anything "wrong" to you.

There are things in Linux, that if you have to ask how to do them, then you should not do them as they involve more skills than we can convey in a forum. Furthermore, in this forum, we give help to people trying to fix problems with their system, we don't necessarily "teach" someone how to become a high-level administrator or hacker. I don't think installing an "unofficial" version of KDE falls in the above category, but a word of caution is warranted as such change may be irreversible and ultimately end up harming your machine.

In short: If someone is "trolling", report them. If someone is giving you advice, then consider it (even if you don't follow it). If you have a question, please spend a few minutes with Google first.

---

### Post by galacticaboy on 2011-04-12
> **3Miro said:**
> If you see "trolling" or "abuse" then you can report it to the mods (there is a "report abuse" button next to every post).

What is not a good idea, is to make me read your rant, when I have never done anything "wrong" to you.

There are things in Linux, that if you have to ask how to do them, then you should not do them as they involve more skills than we can convey in a forum. Furthermore, in this forum, we give help to people trying to fix problems with their system, we don't necessarily "teach" someone how to become a high-level administrator or hacker. I don't think installing an "unofficial" version of KDE falls in the above category, but a word of caution is warranted as such change may be irreversible and ultimately end up harming your machine.

In short: If someone is "trolling", report them. If someone is giving you advice, then consider it (even if you don't follow it). If you have a question, please spend a few minutes with Google first.

Understood! But now I have another question! And feel free to answer however you like! =-] I did what you told me to do, when I rebooted, I got an error message about it not finding a theme or something, it went really quick so I did not have time to write it down, then it took me straight to the terminal, I freaked out because I thought I broke my system. I typed startx and it booted to GUI, but there was no login screen except for the Terminal. What went wrong, I am almost scared to reboot my system again!

---

### Post by 3Miro on 2011-04-12
It probably did not convert your old settings correctly. Try in the terminal:

```
mv .kde .kde_backup
mv .kde4 .kde4_backup
```

I am not sure which one will work, the config files are either in .kde or .kde4, I don't remember which one they used in Kubuntu.

This will reset your KDE settings to default and you should be able to reboot safely.
```
sudo shutdown -r now
```

---

### Post by galacticaboy on 2011-04-12
> **3Miro said:**
> It probably did not convert your old settings correctly. Try in the terminal:

```
mv .kde .kde_backup
mv .kde4 .kde4_backup
```I am not sure which one will work, the config files are either in .kde or .kde4, I don't remember which one they used in Kubuntu.

This will reset your KDE settings to default and you should be able to reboot safely.
```
sudo shutdown -r now
```

That did not work This is the message I get, "Cannot open theme file /usr/share/kde4/apps/kdm/themes/ethias" Then it takes me to the terminal where I type in "startx'. It does not save any of the plasmoids that I Put on my desktop, it resets my desktop and everything on it. I may just have to reinstall and not worry about upgradeing, 11.04 comes with 4.6. But if you have a solution PLEASE tell me! =-] Thanks for your help!
David

---

### Post by 3Miro on 2011-04-12
Something either didn't install correctly or mv .kde did not clean the proper config files. You can take a look at other .something files in your /home/your_username to see if moving them helps (like .config maybe). It is possible that if you have installed custom widgets, they don't upgrade to 4.6 properly and cause plasma to crash on you.

If a package is missing:

Install aptitude:

```
sudo apt-get install aptitude
```

Then use it to search for the missing theme:

```
sudo aptitude search ethias
```

If you find it, you can use apt-get install to install the package.

---

### Post by SeijiSensei on 2011-04-12
Try creating a new user and logging in from that account.  You'll get the default KDE desktop.  Does that work?

At the text-mode prompt, type "sudo adduser username" and follow the prompts.

As I recall 4.6 didn't like my settings either, but renaming .kde and starting over like 3Miro suggests gave me the default desktop again.

---

### Post by galacticaboy on 2011-04-12
Ehh thanks for all your help guys but I just went ahead and reinstalled Kubuntu and I will wait for 11.04 to get KDE 4.6. Much appreciated!
David

---

