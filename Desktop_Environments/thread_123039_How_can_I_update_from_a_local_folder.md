---
title: "How can I update from a local folder?"
date: 2006-01-29
forum: Desktop Environments
---

### Post by Mykas0 on 2006-01-29
First, I have to start by telling you that I am a major newbie.

So, I wanted is... I've saved the contents of my ubuntu cd to the home/cd/ folder. Now, if I want to update using the files stored in this folder, what do I need to do on Synaptic (or what do I have to write in a certain file?) ?


And no, I can't update from the internet.

---

### Post by otey on 2006-01-29
If you have an ubuntu cd, you dont have to copy the files to your harddisk. 

Just go to the package manager at system -> Administration -> Synaptic package manager 
In Synaptics, go to the menu -> Edit -> Add CD-ROM.

---

### Post by Mykas0 on 2006-01-29
No, I don't currently have a CD. I just have the content of the latest CD saved in my disk, in the place I told you!

---

### Post by otey on 2006-01-29
Then go to synaptics and in the menu go to "settings -> repositories"

click on the "add" button and then click on the "custom"

The apt line command should be 

**deb file:///home/YOUR_USERNAME/cd/ breezy main restricted**

---

### Post by Mykas0 on 2006-01-29
Tried that line, but it doesn't seem to add all the packages. Basically, I am searching for the ones related to the "unicorn" driver and all its dependecies.

---

### Post by otey on 2006-01-29
Are you sure they are on the breezy cd? I don't think they are.. You have to go online to get them.

---

### Post by Mykas0 on 2006-01-29
I have no idea if they are or not, but I thought the packages were all in the same CD...

---

