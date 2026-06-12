---
title: "Access the other partitions in FakeRaid"
date: 2009-03-09
forum: General Help
---

### Post by Lasering on 2009-03-09
Hi!

I've installed Ubuntu, through the alternate CD, so that I could installed it on my FakeRAID.

Everything works excellent, except that I cannot access any other partition in the RAID other then those Ubuntu is installed on.

How can I access the other partitions?

Thanks a lot.

---

### Post by fjgaude on 2009-03-10
Well, this will take a little investigating. First show us these:

```
sudo dmraid -ayl
```

After we will have enough info to know how to mount the other drives or partitions. Then we can setup a line in your **fstab** file to auto do everything on booting up.

Here's an article on fakdRAID that might be useful:

[http://users.telenet.be/mydotcom/how...skfakeraid.htm](http://users.telenet.be/mydotcom/how...skfakeraid.htm)

Let us know how things go.

---

### Post by Lasering on 2009-03-10
```
RAID set "pdc_dfehjccjga" already active
RAID set "pdc_dfehjccjga1" already active
RAID set "pdc_dfehjccjga5" already active
RAID set "pdc_dfehjccjga6" already active
```

This is what I got after running that command.

I know that Ubuntu is installed on the last two devices.

---

### Post by Lasering on 2009-03-10
bump

---

### Post by fjgaude on 2009-03-11
Okay, make a mountpoint for the ntfs volume:

```
sudo mkdir /home/ntfs
```

Or wherever you wish to have it placed. Then:

```
sudo mount -t ntfs /dev/mapper/pdc_dfehjccjga1 /home/ntfs
```

See if this mount works, and if so you can place this line as last in **/etc/fstab** file:

```
/dev/mapper/pdc_dfehjccjga1 /home/ntfs ntfs-3g defaults 0  2
```

If you can't mount with **pdc_dfehjccjga1**, try with **pdc_dfehjccjga**, dropping the "1". Also, not sure if you need the "-3g" after ntfs. If not successful, try with or without and see what happens.

Let us know how you are doing... sorry for taking so long to get back to you... have been out of the office.

---

### Post by Lasering on 2009-03-12
Thks a lot worked perfectly :P

Keep up the good work!!!

Thks again!

---

### Post by fjgaude on 2009-03-12
Well, we all keep learning new things, day-by-day. Glad your issue got solved.

---

### Post by Lasering on 2009-05-02
Hi again!

Once more I require your help.

I just upgraded to Jaunty Jacklope redid what you posted and worked seamlessly.

What I'm interessed now is: how to make windows (Vista) see the partitions linux is in. I know that maybe this is not the best place to post this question, but I dont know the "best place".

Thanks once again.

---

### Post by fjgaude on 2009-05-02
Well, I have little knowledge or interest in doing such things in Windows. Wish I could help you, but can't. Try googling...

---

