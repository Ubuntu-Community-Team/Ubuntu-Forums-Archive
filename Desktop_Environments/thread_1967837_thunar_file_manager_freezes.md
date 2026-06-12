---
title: "thunar file manager freezes"
date: 2012-04-28
forum: Desktop Environments
---

### Post by slixz85 on 2012-04-28
hi, i am currently using thunar file manager and it has worked fine for a long time however it seems like out of no where it freezes now. i am pretty sure i haven't uninstalled anything with synaptic since it does this. it is on a machine with no current internet conection so either need to fix it somehow with a usb flash or hopefully it is some code that needs to be fixed. i could install another iso as i do alot to just simply fix it but i have alot of files and also programs that i wouldn't know how to transfer if possible to the new os.

it seems to freeze right when i open it. I can still browse files the hard way for instance using unetbootin browse button to locate an iso or something. i know i can use nautilus by changing the permissions. i already did this but i dont like nautilus not used to it.

thanks to any help.


(p.s.)
if anyone knows as well if it is possible to transfer my games and such to another os patition ext4 it would be much appreciated. i know i could use the temporary file download but i dont have them no longer it has been so long ago. mainly just wanting to get the games from the offline pc transfered to the other ext4.

---

### Post by DeceptiveHornet on 2012-04-28
You could try

sudo apt-get --purge remove thunar
sudo apt-get install thunar

---

### Post by slixz85 on 2012-04-28
> **DeceptiveHornet said:**
> You could try

sudo apt-get --purge remove thunar
sudo apt-get install thunar

my problem is the pc isnt connected to the internet currently. dont get internet installed again for couple months. just mostly play alot of games offline that is why i would also like to know if anyone knows how to move the games from the programs to another os partition.

---

### Post by LewisTM on 2012-04-28
I have experienced this a couple of times before. It was due to a bad thumbnail in my home folder. I used another file manager to move files out of the way until I narrowed it down to a single bad SVG file which I deleted. Thunar stopped freezing.

Cheers!

---

