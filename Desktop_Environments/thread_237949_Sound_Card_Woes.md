---
title: "Sound Card Woes"
date: 2006-08-17
forum: Desktop Environments
---

### Post by syzygy7 on 2006-08-17
I decided to ditch my Windows OS and give Ubuntu a go (I love it!)

The only problem is that the sound card is not working **"No volume control Gstreamer plugins and/or devices found"**

Being new the Linux world I am really not sure where to start, everything else is working perfectly - USB memory stick reader, scanner etc.

I have an IBM PC 300PL (type 6890). Any suggestions appreciated :p

---

### Post by daou on 2006-08-17
Unfortunately I don't have an answer but hopefully [this page]("https://help.ubuntu.com/community/DebuggingSoundProblems") will.

---

### Post by john.ennew on 2006-08-19
I've been pasting this around the various forum posts I looked at whilst tearing my hair out trying to solve it...

OK, I found a fix for me

There is a user group called audio and all users which are to have control of the audio device must be a member of that group. I have no idea how my user account stopped being a member of that group, but adding it back and restarting the computer brought back the sound.

Work instructions:
System->Administration->Users and Groups
Choose the Groups Tab
Make sure the box "Show all users and groups" is ticked and scroll down the window to find the audio group (it's not in alphabetical order)
Highlight it and click Properties
Add all group members which need audio by highlighting the name in the left collumn and clicking add so they appear in the right collumn.
Click OK, OK and restart the computer.

Hope this helps someone,
John

---

