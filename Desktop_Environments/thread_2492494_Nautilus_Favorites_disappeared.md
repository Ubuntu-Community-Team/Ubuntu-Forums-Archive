---
title: "Nautilus Favorites disappeared"
date: 2023-11-13
forum: Desktop Environments
---

### Post by hakelm on 2023-11-13
My Nautilus file manager Favorites have suddenly disappeared. This has also happened to Nemo.
How can I get it back?
Thanks in advance for any tip
H
Using Ubuntu 22,04

---

### Post by hakelm on 2023-11-14
And suddenly, today, Favorites appears again, in Nautilus and in Nemo but I can't add anything.

---

### Post by Claus7 on 2023-11-15
Hello,

do you mean starred? Opening nautilus I cannot see any favorites, yet using 23.10. Is this a bookmark or something? Actually trying to use starred folder by right clicking a file and choosing starred, this option was not available. I suppose that an update might broke the functionality.

Regards!

---

### Post by hakelm on 2023-11-16
Presently I have both Favorites and Starred and they are different. I can, however, not add anything to Favorites,

---

### Post by ajgreeny on 2023-11-16
Does  nautilus (files) use bookmarks the same as other gtk file-managers and are they the same thing as your favourites?
I haven't used gnome or nautilus since gnome2 disappeared all those years ago.

Do you still have a file ~/.config/gtk-3.0/bookmarks as other gtk systems seem to have?
If so, what is the content of that file?

---

### Post by hakelm on 2023-11-16
Yes, I have  ~/.config/gtk-3.0/bookmarks with the content below. Another user on my system has the same issue.

file:///home/he/Dokument Dokument
file:///home/he/Musik Musik
file:///home/he/Bilder Bilder
file:///home/he/Video Video
file:///home/he/H%C3%A4mtningar Hämtningar
file:/// /
file:///home/he/dok/ny/p/hep/test test
file:///home/he/dok/ny/PRIVAT PRIVAT
sftp://root@192.168.1.118/klipp klipp
sftp://192.168.1.104/var/lib/motion motion
file:///home/he/dok/ny ny
sftp://192.168.1.104/ / på 192.168.1.104
sftp://192.168.1.105/ / på 192.168.1.105
sftp://192.168.1.106/ / på 192.168.1.106
sftp://192.168.1.108/ / på 192.168.1.108
sftp://192.168.1.109/ / på 192.168.1.109
sftp://192.168.1.27/ / på 192.168.1.27
sftp://he@192.168.1.118/home/he he118
sftp://root@192.168.1.118/home/he root118
sftp://192.168.1.117/ / på 192.168.1.117
file:///home/he/dok/ny/p/picc/PIC PIC
file:///home/he/dok/ny/p/picc picc
file:///home/he/dok/ny/p/picc/funkar funkar
file:///home/he/dok/ny/PRIVAT/H%C3%85KANDIV/t%C3%A4nder/tungan tungan
sftp://192.168.1.108/home/he 108he
file:///home/he/dok/ny/p/picc/funkar/schablon%20(kopia).X0/dist/default/production production
sftp://192.168.1.118/x/vakt/smedbild smedbild
file:///5t 5t
sftp://192.168.1.117/home/he he

---

### Post by Claus7 on 2023-11-16
Hello,

I created both a folder under Documents and a corresponding bookmark named fav and the result under ~/.config/gtk-3.0/bookmarks is the following:
file:///home/user_name/Documents/fav
file:///home/user_name/Documents
file:///home/user_name/Music
file:///home/user_name/Pictures
file:///home/user_name/Videos
file:///home/user_name/Downloads

I deleted the folder under Documents and the bookmarks place complained that something went wrong. Have you by any chance created a Favorites folder, added it to bookmarks and then accidentally changed its position/deleted it and you are having the problem you mention?

Regards!

---

