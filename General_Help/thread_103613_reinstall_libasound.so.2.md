---
title: "reinstall libasound.so.2"
date: 2005-12-14
forum: General Help
---

### Post by MetalHannes on 2005-12-14
I have accidentally destroyed or damaged or made on some other way libasound.so.2 unusable. When i try to log it logs meoff again sayong there might be some problems because my session lasted shorter than 10 sec. Viewing the Error log i found out that libasound.so.2 was corrupted.
I tried to install it over the terminal (where i was able to log in) with the following commands:
sudo apt-get install libasound
sudo apt-get install libasound.so
sudo apt-get install libasound.2
sudo apt-get install libasound.so.2

sudo apt-get update installed nothing.
Btw way i may be not able to use my computer for the next 2 days.

Thx very much

Hannes

---

### Post by MetalHannes on 2005-12-15
Yeah because the command was
sudo apt-get install libasound2
silly me:rolleyes: :rolleyes: 

Hannes

---

### Post by Allex1 on 2008-05-08
Great post, I have exactly the same issue, I cannot install libasound as it says it's already there, I'll probably remove it and install it again, thx for the tip

---

