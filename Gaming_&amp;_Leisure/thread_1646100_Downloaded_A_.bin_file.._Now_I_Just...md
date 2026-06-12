---
title: "Downloaded A .bin file.. Now I Just..?"
date: 2010-12-15
forum: Gaming &amp; Leisure
---

### Post by BreezeWater on 2010-12-15
I recently downloaded PlaneShift for my laptop.
There is no direct download.. only a torrent.
Once the download is completed I used Transmission to open it and it came as a .bin file!
I have saved it to my desktop for easy access.

It started kinda easy.. So I figured it would end up that way.
I went into my terminal and typed 'cd Desktop'
Then I 'sudo chmod'
Then When I type './PlaneShift.bin' terminal says that it can execute a binary file. 
How do I execute this file??

Please Help.

---

### Post by alexandrius on 2010-12-15
You should have written "**sudo chmod +x PlaneShift.bin**"

---

### Post by BreezeWater on 2010-12-15
Alrite.. When I Did that I was prompted for my password. When I entered my sudo pw nothing happened.
Then I entered "**./Planeshift.bin**"
and It still says that I cannot execute a binary file

---

### Post by Zzl1xndd on 2010-12-15
Right click the .bin file > Select Permissions and make sure the option to execute is checked. Then you should be able to just drag the bin into the terminal (this will enter the full path, you will likely need to hit backspace one as drag and drop normally adds an extra space). Hope this helps.

---

### Post by BreezeWater on 2010-12-15
hmm.. didnt know that you could drag items into terminal. But the file was already checked as executable. When I Dragged the file to the desktop and deleted the space, I pressed enter and was still told that the file was binary and that it could not be executed

---

