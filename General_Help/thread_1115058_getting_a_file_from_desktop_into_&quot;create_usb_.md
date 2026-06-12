---
title: "getting a file from desktop into &quot;create usb iso&quot;"
date: 2009-04-03
forum: General Help
---

### Post by jesse c on 2009-04-03
I have posted similar question before and got a lot of feedback/help that encouraged me to go the unetbootin route,but i really would like to know how i can get a file (in this case a Jaunty beta) that i downloaded and appears on my desktop,into the Intrepid application 'create a usb start up disk'.I have somehow accomplished this same task a few weeks back creating a eeebuntu usb flash for my netbook using a step by step tutorial so i thought id try a Jaunty(beta) flash for kicks in my desktop but i cant figure out how to get the download into the create window of app.At this point im actually going to buy a live cd from OsDisc in a couple of weeks,but i would like to how to do it for future attempts.
Thanks  JESSE C

---

### Post by anjilslaire on 2009-04-03
I just used this the other day to create a bootable usb with the Jaunty beta.
1. Launch the "create usb startup disk"
2. where it says "Please insert a CD or select Other", select Other
3. Bowse to where your Jaunty ISO is on your desktop and select it
4. Select your destination usb drive, and select "Make startup disk"

---

### Post by James_Lochhead on 2009-04-03
[LIST=1]
[*]Put the iso on your desktop.
[*]Open the program.
[*]Select the "Other" option.
[*]Navigate to your desktop. Since this program has been started as a root user you are now on the roots desktop.  Press the little icon of something being written and type / in the location bar. Now you need to move to your home directory, this should be something like /home/jesse/. In that folder you will find another folder for your Desktop.
[*]Select the iso and click ok.
[*]Now simply highlight your memory stick and press ok again.
[/LIST]

---

