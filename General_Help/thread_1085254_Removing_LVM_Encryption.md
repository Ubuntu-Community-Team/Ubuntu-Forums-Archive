---
title: "Removing LVM Encryption"
date: 2009-03-02
forum: General Help
---

### Post by Thundara on 2009-03-02
I've spent the past couple of days setting up an old computer to be a media box for the house, but while everything looks nice on the inside, I stupidly set a password for the LVM, so every time I start up, I require a monitor in order to enter the password. Is there any quick way I can remove this password and decrypt the partition if needed?

---

### Post by Thundara on 2009-03-04
After looking into this a bit, I found myself presented with two options:
[LIST=1]
[*]Create a new physical volume on the disc and transfer everything over, perhaps a bit too complex for a simple mind like mine
[*]Use cryptsetup to remove the encryption on /dev/sda1, something I'm much more inclined to do since it hopefully would not involve moving tons of data around.
[/LIST]
Does anyone have any suggestions on how to go about doing either? All help is appreciated :D

Edit: After a bit of time spent on this problem, I've found that the easiest solution was to go into:
/usr/share/initramfs-tools/scripts/local-top/cryptroot
and edit the line:
```
$cryptkeyscript "$cryptkey" | $cryptcreate --key-file=- ; then
```
to:
```
echo -n "PASSWORD" | $cryptcreate --key-file=- ; then
```
Which put the password straight into the decryption part of the code, rather than prompting the user. It's hackish, and I'd definitely like to say to remember to put "echo **-n**" so it doesn't mess it up and lock you out, but it works, which is what I was looking for.

---

### Post by harry71194 on 2009-09-08
Thanks, this is the best answer I could find !! :)

---

### Post by ruipedroca on 2010-07-26
Hi,

It didn't work for me:(
I'm on 10.04 and I have to introduce a passphrase (not a key file).

Can you shed some light, please?

Regards

---

