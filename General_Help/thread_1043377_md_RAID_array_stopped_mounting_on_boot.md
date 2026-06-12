---
title: "md RAID array stopped mounting on boot"
date: 2009-01-18
forum: General Help
---

### Post by GurneyHalleck on 2009-01-18
Here's a problem that I managed to solve, so I'm posting here in the hope that it may help if someone encounters the same thing in future.

I've been using Ubuntu 8.04 since I built my new machine in June last year. I used md to create a pair of RAID 1 arrays for my home and web development directories. The md volumes were mounting automatically on boot every time without problems until the end of December. Then suddenly I was getting an error message along the lines of "home directory not found".

At first I thought the whole thing had failed somehow, but it turned out that mdadm simply wasn't mounting the /dev/md0 volume that represented the RAID array. Changing session to Failsafe Terminal (and allowing /root to become my home directory temporarily) I could see that the partitions were all still there, but they weren't being assembled into a RAID array.

Looking at /etc/mdadm/mdadm.conf I noticed that the file was more or less empty. There was no mention of any device paths or UUIDs, and it looked like the file had not been changed since I first setup the arrays in June.

After a bit of hunting around online (from, ahem, Windows) I found out that the following (typed into the failsafe terminal) would get things mounted temporarily:

```
sudo mdadm --assemble /dev/md0 /dev/sda5 /dev/sdb9
sudo mdadm --assemble /dev/md1 /dev/sda4 /dev/sdb3
sudo mount -a
```

(NOTE: You must know which partitions are used to create each array, and change the above to match your setup. This is the sort of information that isn't easy to remember, and I had to resort to trial and error, attempting to mount each device and using the error messages to work out which ones were RAID components.)

Once you've mounted the RAID arrays this way, you can exit the Failsafe Terminal, then change session back to GNOME and login properly. However, this only keeps the RAID arrays mounted until you reboot, and then you'll have to mount the arrays yourself again.

To get mdadm to mount the RAID arrays automatically, I had to modify the /etc/mdadm/mdadm.conf file so that it contained

```
DEVICE /dev/sda5 /dev/sdb9
DEVICE /dev/sda4 /dev/sdb3
DEVICE partitions
```

at the top, and then

```
ARRAY /dev/md0 devices=/dev/sda5,/dev/sdb9
ARRAY /dev/md1 devices=/dev/sda4,/dev/sdb3

```

at the end of the file.

So now things are back to normal. But if anyone can tell me why my arrays were mounting fine for six months with an empty config file, or why they suddenly stopped mounting automatically, I'd be very interested to have the mystery solved.

---

### Post by fjgaude on 2009-01-18
Well, for one thing the kernel **md** module can assembly an array from the UUID of the drives that make up the array. This UUID is different from the UUID used to mount drives.

So if you had removed **mdadm** with **apt-get**, deleted the non-valid **mdadm.conf** file, then re-booted, and next re-installed mdadm, a valid mdadm.conf file would have been auto-created.

Many ways to skin the cat, eh?

I have no idea why it stopped working except it is likely some change made without knowing its effect. <smile>

---

### Post by GurneyHalleck on 2009-01-20
Well, it was working one minute, next time I booted it was no longer doing its thing.

The only thing I had been doing was enabling and then disabling the wireless interface. I didn't even download any software updates. So I'm not sure what would have triggered the change.

Computers, eh?

---

