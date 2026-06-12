---
title: "Disk Drive Error on start up ?"
date: 2011-06-16
forum: Dell Ubuntu Support (CLOSED)
---

### Post by anubhav2k on 2011-06-16
Whn i turn on my laptop, dell studio 1555 on which i have double boot installed win 7 nd ubuntu.... it gives an error

The disk drivce for /windows is not ready yet or not present

continue
s - skip
m - manually restore 


how can i fix that.. plz help , m new to ubuntu but i like it ...

---

### Post by mörgæs on 2011-06-16
This is not a problem specific for Dell. You will get better answers if posting in 'general help'.

Have you been new to Linux since october 2008?

---

### Post by jerrrys on 2011-06-16
i do not run windows so i don't know, but can point you here

[http://www.googlubuntu.com/results/?cx=006238239194895611142%3Au-ocqbntw_o&cof=FORID%3A9&ie=UTF-8&q=The+disk+drive+for+%2Fwindows+is+not+ready+yet+or+not+present&as_qdr=all&sa=Google+Search&lang=en#1076](http://www.googlubuntu.com/results/?cx=006238239194895611142%3Au-ocqbntw_o&cof=FORID%3A9&ie=UTF-8&q=The+disk+drive+for+%2Fwindows+is+not+ready+yet+or+not+present&as_qdr=all&sa=Google+Search&lang=en#1076)

---

### Post by Rubi1200 on 2011-06-16
What happens if you press S to skip?

I recommend you post the results of the boot info script so we can get a better idea of what is going on:

Boot the Ubuntu Live CD/USB. Choose the option "Try Ubuntu without any changes." Once the desktop loads come back here and do the following:

1. Download the boot info script which is in a zipped file. There is a link in my signature.
2. Once downloaded, move the boot info script by either copying or dragging and dropping the zipped folder onto the desktop and unzip the contents by using right-click Extract here.
3. Open the folder and copy the script to the desktop (you can also drag and drop if you like)
4. Open a terminal and run the following command

```
sudo bash ~/Desktop/boot_info_script.sh
```

This will create a RESULTS.txt file on the desktop. Paste the entire contents of that file back here in a new post. Once pasted highlight all text and click the # sign on the toolbar to place code tags around the text.

---

### Post by anubhav2k on 2011-06-17
> **mörgæs said:**
> This is not a problem specific for Dell. You will get better answers if posting in 'general help'.

Have you been new to Linux since october 2008?


new bcoz i made an account in 2008 whn i tried to install ubuntu earlier ... but thn i bought new laptop which had a new win vista , tht time i dint want to disturb my original os, now i have formatted my laptop :p

---

### Post by anubhav2k on 2011-06-17
> **Rubi1200 said:**
> What happens if you press S to skip?

I recommend you post the results of the boot info script so we can get a better idea of what is going on:

Boot the Ubuntu Live CD/USB. Choose the option "Try Ubuntu without any changes." Once the desktop loads come back here and do the following:

1. Download the boot info script which is in a zipped file. There is a link in my signature.
2. Once downloaded, move the boot info script by either copying or dragging and dropping the zipped folder onto the desktop and unzip the contents by using right-click Extract here.
3. Open the folder and copy the script to the desktop (you can also drag and drop if you like)
4. Open a terminal and run the following command

```
sudo bash ~/Desktop/boot_info_script.sh
```

This will create a RESULTS.txt file on the desktop. Paste the entire contents of that file back here in a new post. Once pasted highlight all text and click the # sign on the toolbar to place code tags around the text.



its giving following error, i have placed the file on desktop

ubuntu@ubuntu:~$ sudo bash ~/desktop/boot_info_script.sh
bash: /home/ubuntu/desktop/boot_info_script.sh: No such file or directory
ubuntu@ubuntu:~$

---

### Post by mörgæs on 2011-06-17
The command shoud be written with a 'D', not 'd'.

---

### Post by Coltman151 on 2011-06-17
I installed a brand new drive and did a complete clone over to it and had a similar problem. What i figured out was my old hard drive (decided to use for extra storage) was taking longer to spin up and just waiting a few seconds fixed it.

Yes, its a little annoying when it does it, but my problem isn't fatal so I left it at that.

Hope this helps.

---

### Post by anubhav2k on 2011-06-17
> **mörgæs said:**
> The command shoud be written with a 'D', not 'd'.

I tried with D also instead of d, same error :(

---

### Post by Rubi1200 on 2011-06-17
Did  you extract the bash file from the zipped folder?

If yes, then open the folder it creates and copy that file again to the desktop and then run the command.

---

### Post by anubhav2k on 2011-06-17
> **Rubi1200 said:**
> Did  you extract the bash file from the zipped folder?

If yes, then open the folder it creates and copy that file again to the desktop and then run the command.

ya did the same extracted the zipped file on desktop, it had 2 files copied them on desktop, thn i did run that command but that error

---

