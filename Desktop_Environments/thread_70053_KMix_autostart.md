---
title: "KMix autostart"
date: 2005-09-28
forum: Desktop Environments
---

### Post by Panthios on 2005-09-28
Hi.

I don't understand why KDE don't have a volume control near systray at start - like Gnome / Windows.

I want KMix to autostart in the systray - but how to do that?

Sorry for my english.
Best regards

---

### Post by beefsprocket on 2005-09-28
Firstly, it should run by default with a new install. Secondly, if it doesn't, once you have your sound working all you should have to do is run it. When you next logout make sure that it is still running when you logout. When closing kmix, don't choose quit from the menu, just the close window button in whatever decoration you are using.

---

### Post by Panthios on 2005-09-28
[QUOTE=beefsprocket]Firstly, it should run by default with a new install. Secondly, if it doesn't, once you have your sound working all you should have to do is run it. When you next logout make sure that it is still running when you logout. When closing kmix, don't choose quit from the menu, just the close window button in whatever decoration you are using.[/QUOTE]

It didnt show up on a new install.
And by closing KMix down to systray, then log out / log in, does not help, cause I have chosen to start with a new session via Control Panel.
Another method to autostart KMix?

Best regards

---

### Post by Panthios on 2005-09-29
Bump - please?
Somebody must have an answer.

---

### Post by Simian on 2005-09-29
[QUOTE=Panthios]Bump - please?
Somebody must have an answer.[/QUOTE]

I had exactly the same problem once whilst using Suse (Yast :mad: ). What I did was start kmix. Then click save this session (or something like that) just abouve "log out" on the Kmenu. Then the everytime you log in Kmix should be there in the sys tray (kicker).

As you say, it is strange!

---

### Post by Simian on 2005-09-29
Actually there is a difference. You are set to Start new session upon each login. I had mine set to load previously saved session upon each login. That gives you the option "Save Session" on you Kmenu.

---

### Post by jpmontalbo on 2005-10-25
Hello Panthios, I also have my kde start with new sessions. This is how I make kmix start automatically when you login. 1. Go to your home folder 2. Click on **View** at the top and then click on **Show Hidden Files** 3. you will now see hidden directories, go to **.kde** folder. after that, go to **autostart** folder 4. right click on blank area and click **create new** then go to **link to application** 5. in blank default is link to application, you can name it kmix or whatever you like to remind you what it is. 6. click on tab that says application, again populate name section with whatever you want, then on the command section paste this in **kmix -caption "%c" %i %m** 7. Finally click ok and from now on, kmix will start automatically at kde startup. :p Hope I gave this advice in time.

---

### Post by devnulljp on 2006-04-16
I have the opposite problem - I don't have kmix in  ~/.kde/Autostart yet the kmix window pops open every login.
Even if I kill kmix, save session, log out and log in again.
Any idea how to disable that behaviour?

---

