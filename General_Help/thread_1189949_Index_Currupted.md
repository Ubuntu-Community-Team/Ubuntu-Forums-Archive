---
title: "Index Currupted"
date: 2009-06-17
forum: General Help
---

### Post by chamithmalinda on 2009-06-17
A error message appeared "Tracker". And tell that there was a indexing  error and ask for perform re indexing when click that same error occurred again and again. Is there a solution Please help me. I attached the error message.....................:(:(

---

### Post by gunksta on 2009-06-17
Sometimes Tracker gets all confused and manages to corrupt it's database. There are, however, some easy fixes.

1) If you never use Tracker, and don't see yourself using it in the future, you can just turn it off.  Go to System->Preferences->Startup Applications. Scroll down and un-check Tracker and Tracker Applet. Then stop all active tracker processes. System->Administration->System Monitor. Organize things alphabetically. Go find tracker and kill them all. (Should only be two items in the list)

Note: This is a fairly extreme measure. More and more apps are starting to work with Tracker so it may be worth actually fixing.

2) To actually fix this. You can first kill everything related to tracker (see above for how to end/kill running processes). Then, reset it. Open up a terminal (or use nautilus). We need to go to the ~/.local/share folder. In Nautilus, you can go to View-> Show Hidden Files and go to your home directory. From there browse to .local/share.  In this folder you should see a folder called tracker. Delete it. Now restart tracker. You can just restart gnome to make things easier (although it's not strictly necessary).

I have had problems with Tracker in the past. I use Evolution as my mail client and I am attached to a rather large gmail account via IMAP. Tracker struggled indexing all of this and it's attempts repeatedly led to the corruption you have found. If you are connected to a large IMAP account, it might be worth your time to tell Tracker to NOT index this. Go to System->Preferences->Search & Indexing. When this starts up, go to the tab labeled email.

Disable Evolution indexing. By wiping out my existing Tracker profile AND telling Tracker to ignore Evolution, I was able to end my Tracker problems.

---

### Post by valex on 2009-06-17
1. Enter the directory "~/.config/autostart", create it if it does not exist
         2. Create a file named trackerd.desktop
         3. Paste the following into the file, save and exit 

      [Desktop Entry]
      Encoding=UTF-8
      Name=Tracker
      Hidden=true

This should be disable tracker for your user.

---

