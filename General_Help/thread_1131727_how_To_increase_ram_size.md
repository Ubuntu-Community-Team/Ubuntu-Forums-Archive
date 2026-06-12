---
title: "how To increase ram size"
date: 2009-04-21
forum: General Help
---

### Post by suresh_vandiyur on 2009-04-21
i have 512mb ram.. i need to change my ram 512 to 1gb.. how to change the ram size? any one know means reply me...

---

### Post by cyran on 2009-04-21
RAM is a piece of hardware. You'd have to buy more or bigger RAM cards from a store (online or physical) and install them inside the computer.

What kind of RAM you need to buy depends on whether you have a laptop or a desktop, and what speed of RAM it can use. (DDR, DDR2, or DDR3 being the major types, each with several different speeds).

---

### Post by raedbenz on 2009-04-21
go and buy new RAM and install it. 
check:
[http://www.amazon.co.uk/s/ref=nb_ss_w_h_?url=search-alias%3Daps&field-keywords=pc+ram&x=0&y=0](http://www.amazon.co.uk/s/ref=nb_ss_w_h_?url=search-alias%3Daps&field-keywords=pc+ram&x=0&y=0)

---

### Post by Lunx on 2009-04-21
> **suresh_vandiyur said:**
> i have 512mb ram.. i need to change my ram 512 to 1gb.. how to change the ram size? any one know means reply me...

Buy another stick of 512mb RAM? Are you using a single 512mb stick, or two 256 sticks? DDR2 RAM is pretty cheap these days. Be aware there are different types required depending on whether it's a laptop or a desktop system as the module sizes are different. Some early Laptops did use RAM made for desktops, but these old systems are now few and far between. Your manual for your motherboard is worth referring to as it will tell you what RAM is compatible.

---

### Post by prshah on 2009-04-21
> **suresh_vandiyur said:**
> i have 512mb ram.. i need to change my ram 512 to 1gb.. how to change the ram size?

You need to know

a) Type of RAM
b) No of slots used
c) No of slots available

The following command will give you this information; post back the output if you need it to be explained further.

Open a terminal (Applications-Accessories-Terminal) and give the command```
sudo lshw -C memory | grep -A 50 -i "system memory"
```

---

### Post by suresh_vandiyur on 2009-04-23
> **prshah said:**
> You need to know

a) Type of RAM
b) No of slots used
c) No of slots available

The following command will give you this information; post back the output if you need it to be explained further.

Open a terminal (Applications-Accessories-Terminal) and give the command```
sudo lshw -C memory | grep -A 50 -i "system memory"
```
in redhat we increase swap size means first we delete older swap and then we make new size swap and edit in /etc/fstab. i no need physical device. if i changing the swap means which file should be edit?.. what is the commands for changing swap size.. anyone know means reply me...

---

### Post by prshah on 2009-04-23
> **suresh_vandiyur said:**
> how to change the ram size

> **suresh_vandiyur said:**
> in redhat we increase swap size means first we delete older swap and then we make new size swap and edit in /etc/fstab. 

Do you want to change your RAM size or Swap size?

You have to follow a similar method in Ubuntu as in RedHat. However, you have some options:

a) Boot off a live CD, give the terminal (Applications-Accessories-Terminal) command```
sudo swapoff -a
```, then use System-Administration-Partition Editor to Resize the swap partition. You may need to create space for it by resizing following (not recommended) or preceding (recommended) partitions.

b) You may benefit from creating a swap FILE rather than a swap partition. The advantage is simply that you do not need to mess with your partitions. Post back if you want details on this.

c) Why do you want to increase your swap space? Increasing swap space will not necessarily make your computer faster.

---

