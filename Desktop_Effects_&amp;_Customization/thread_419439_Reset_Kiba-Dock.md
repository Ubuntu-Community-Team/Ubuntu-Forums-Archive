---
title: "Reset Kiba-Dock"
date: 2007-04-23
forum: Desktop Effects &amp; Customization
---

### Post by Tyriel on 2007-04-23
Hi Guys, I have searched these forums and the web for a while now for a solution with no luck so I am now posting here in the hope that someone hear knows how to do this.

I installed Kiba-Dock and had it running well.  However while playing around with its settings to see what it was capable of I seem to have broken something.  Basically I  made all of the icons rest on top of each other.  

I thought no problem I'll just delete the .kiba-dock directory to reset it and start over again.  However it seems that it did not reset it but instead just removed its links.  Now I have an invisible dock that I can not configure.

So back to the question, do any of you know how to reset Kiba-Dock to its original settings?  Thanks in advance.

---

### Post by ckipel on 2007-04-23
There isn't a way to reset it as far as my search on the internet goes.. However, in your terminal, type gset-kiba and it should open up the settings window for you to play with. Try to undo the settings you set and it should work fine.

---

### Post by Tyriel on 2007-04-24
Thanks for the reply ckipel.  Your post and another from a different thread game me the idea to create a new user account so Kiba-Dock would load on it with the default settings.  I then used the systray icon to save it as a default profile.

I then copied the .kiba-dock directory from the new account to my real one and once again used the systray icon to load the saved them hence resetting my setup.  I know this is a round about way of resetting it but it worked for me.

---

