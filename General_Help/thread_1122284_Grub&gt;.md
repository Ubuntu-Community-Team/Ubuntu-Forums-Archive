---
title: "Grub&gt;"
date: 2009-04-10
forum: General Help
---

### Post by noelc on 2009-04-10
Hi,

I am looking to mave away from XP and have downloaded and created a dul boot so I can familiarise myself with Ubuntu. When I try to load Ubuntu I get a black screen wiht the word grub>

Its obvioulsy waiting for a command from me? But what?

Can anyone help

---

### Post by meierfra. on 2009-04-10
Something must have  went wrong during the install.  Are you able to type at the black screen with "grub"?  (I assume not)

In order to get a clearer picture of your setup, I suggest to boot from the Ubuntu LiveCD and  download the Boot Info Script to  your desktop:

[https://sourceforge.net/projects/bootinfoscript/]("https://sourceforge.net/projects/bootinfoscript/")

Then open a terminal (Applications > Accessories > Terminal) and type:

```
sudo bash ~/Desktop/boot_info_script*.sh
```

That will create a "RESULTS.txt" file in the same directory from where the script is run, namely your desktop; please copy/paste the contents of the RESULTS.txt file to your next post,  highlight the copied text, and click the pound/hash sign "#" graphic button in the Ubuntu forum message box so that the text will get "code" tags put around it. The results of that script will help clarify your setup and hopefully what the solution to your booting problem might be.

---

### Post by Thura on 2009-04-10
Umm, how comes, most of the time, ubuntu installation just works out of box. 
Can you boot Windows XP ?

Never mind ...
When you got into grub >, do these one-by-one ...
```
find /boot/grub/stage1
```
This will output a message, like "(hd?,?)" where ? can be any numbers ...
You need to use that in the next command ...

```
root (hd?,?)
```
Don't forget (hd?,?) is the output from previous command.

```
setup (hd0)
```

```
quit
```

Then if everyth works fine, you can boot ubuntu now ...

---

### Post by noelc on 2009-04-13
Yhanks Thura,

I tried but received a message saying error 15 file can not be found found. looks like I will need to download again and try a second time?

---

