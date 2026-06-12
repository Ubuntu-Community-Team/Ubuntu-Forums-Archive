---
title: "prbolems while running GUI applications using CRONTAB"
date: 2008-12-30
forum: General Help
---

### Post by arunprasad13 on 2008-12-30
hi..i have ubuntu edgy 6.10 ..i m not able to run azureus at a particular time in gui...i have copied the different option which i tried and pasted here.

arun@arun-desktop:/opt/azureus$ sudo crontab -e
crontab: installing new crontab
arun@arun-desktop:/opt/azureus$ sudo crontab -l
# m h dom mon dow command
39 00 * * * export DISPLAY=:0 && ./azureus
arun@arun-desktop:/opt/azureus$ sudo crontab -e
crontab: installing new crontab
arun@arun-desktop:/opt/azureus$ sudo crontab -l
# m h dom mon dow command
41 00 * * * export DISPLAY=:0 && /opt/azureus/azureus
arun@arun-desktop:/opt/azureus$ sudo crontab -e
crontab: installing new crontab
arun@arun-desktop:/opt/azureus$ sudo crontab -l
# m h dom mon dow command
43 00 * * * env DISPLAY=:0.0 /opt/azureus/azureus
arun@arun-desktop:/opt/azureus$ sudo crontab -e
crontab: installing new crontab
arun@arun-desktop:/opt/azureus$ sudo crontab -e
crontab: installing new crontab
arun@arun-desktop:/opt/azureus$ sudo crontab -l
# m h dom mon dow command
45 00 * * * env DISPLAY=:0.0 ./azureus
arun@arun-desktop:/opt/azureus$

---

### Post by dcstar on 2008-12-30
> **arunprasad13 said:**
> hi..i have ubuntu edgy 6.10 ..i m not able to run azureus at a particular time in gui...i have copied the different option which i tried and pasted here.
........

Do not run mixed commands, run a script that contains commands.

There are many posts already in the forums on what to do.

---

### Post by arunprasad13 on 2008-12-30
hi..i did ample searching before posting the thread..i tried various it in various combinations..but none of the really work for me...i think i m doing some basic mistake

when i read other forums regarding this ,the same format which i have tried is said to be working...whereas it doesn work for me..
thats the reason why i pasted the code specifically instead of asking a generic doubt as i did last time around..i have throughly utilised the help pages and forum links which was given to me in t he previous threats besides my own efforts to fix the problem

---

### Post by dcstar on 2008-12-30
> **arunprasad13 said:**
> hi..i did ample searching before posting the thread..i tried various it in various combinations..but none of the really work for me...i think i m doing some basic mistake

when i read other forums regarding this ,the same format which i have tried is said to be working...whereas it doesn work for me..
thats the reason why i pasted the code specifically instead of asking a generic doubt as i did last time around..i have throughly utilised the help pages and forum links which was given to me in t he previous threats besides my own efforts to fix the problem

A forum search of "azureus cron" brings up heaps of posts, a lot which have exactly what you need.

I suggest you try again.

---

### Post by ju2wheels on 2008-12-30
Be sure that when you manually edit the crontab file that you leave an empty line at the end below all your commands or it wont execute any of the commands at all.

---

### Post by dagnabit dang doohickey on 2008-12-30
Add your username to the cron.allow file:
```
sudo bash -c 'echo "*username*" >> /etc/cron.allow'
```
Edit your crontab (without sudo):
```
crontab -e
```
Add your cron job:
```
45 00 * * * env DISPLAY=:0. /opt/azureus/azureus
```
The above cron job assumes azureus is located in /opt/azureus/ and should be launched at 12:45 AM.

---

### Post by arunprasad13 on 2008-12-30
thank you dagnabit dang doohickey...!:D although i saw in few posts that the cron.allow file should be edited..i thot it was only when when such a file existed..so i never followed that part...thanks for your guidance...my problem is fixed..!

---

