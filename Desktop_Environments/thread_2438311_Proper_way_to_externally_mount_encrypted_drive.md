---
title: "Proper way to externally mount encrypted drive"
date: 2020-03-09
forum: Desktop Environments
---

### Post by kingreagan41 on 2020-03-09
Hello.  I hope that I am posting in the correct location.  If not, please direct me to the correct forum.

I have a Lenovo P71 and the MB recently failed.  I have Ubuntu 18.04 desktop installed (fully patched as of last Thursday) on the NVMe drive.  When I did the initial installation of Ubuntu and setting up the LVM, I did do the drive encryption through the Ubuntu setup installer.  Every time I booted my computer, I would get the Ubuntu-esque drive encryption prompt before it would go through the rest of the boot process and bring me to the main desktop login screen.  It's not looking like the laptop is going to be repaired for several weeks, so I was contemplating mounting the NVMe drive via USB, however, I would appreciate some guidance before I start playing with the drive.

I pulled the drive before the first service hack took my laptop apart to tell me the mb was gone and needed to be replaced.  The electrical smell and inability to power on were both dead giveaways.

First question, is the LVM encryption tied to the BIOS or the TPM chip on the mb?  If so, I believe that is game over.
If NO, then is it safe to mount the NVMe using an adapter?
Would someone be able to provide a referral to a proper/current mounting process for this situation...assuming it's OK to do so.

If I'm missing anything else that I should be asking or that I should be concerned with when trying to access the data on this drive, I'm all ears and appreciate the feedback.
I'm not at the Linux Developer level or a hardware engineer, but I am an IT professional for over 30 years and have been using Ubuntu as my primary desktop for over 12 years.  I'm not generally afraid of working through any situation, but my rule of thumb is to be very careful when working through a process where the data is at risk of being lost.  I do have backups, but they are significantly divergent after only a few weeks.  It would be greatly helpful to be able to mount and offload the key files until the mb is repaired.

Anyone's help is greatly appreciated.

---

### Post by TheFu on 2020-03-09
I've not done it with NVMe, but I have with SATA HDDs and SATA SSDs.  My notes:
```
# **This is NOT a script.** It is manual steps for opening a LUKS encrypted
# partition and looking for LVM LVs inside, which can be mounted and 
# accessed for any needs.
# Whenever using encryption, backups that can be restored perfectly are
# mandatory.  Any physical or logical issue with LUKS can completely
# destroy all access.

# Convenience variables - change for your needs
DEV=/dev/sdz5
PV=c7205467

# Need to install a few packages if a "Try Ubuntu" desktop environment
# is being used. This also could apply to a recovery system boot.
sudo apt install lvm2 cryptsetup-bin

# Open the container
# Must know the passphrase to unlock the LUKS encrypted 
# container. This is usually just inside a full partition.
# The options may be deprecated on newer OSes.
sudo cryptsetup luksOpen $DEV $PV

# Activate the LVM VGs
# LVM2 is used with Ubuntu full disk encryption. -ay order matters.
sudo vgchange -ay

# Create some temporary mount points.
# A mount point is just an empty directory
sudo mkdir /mnt/slash /mnt/home /mnt/Stuff

# Use lsblk to get a list of the LVs available
 lsblk -e 7 -o name,size,type,fstype,mountpoint

# Using the found LVs, mount them somewhere
sudo mount /dev/mapper/$PV*home /mnt/home
sudo mount /dev/mapper/$PV*Stuff /mnt/Stuff

# if the storage doesn't mount, perhaps run an fsck on the LV devices.

# access the storage as needed.  Probably want to make a backup if 
# you had to use these steps to get it mounted, right?
```

Good luck.

---

### Post by kingreagan41 on 2020-03-11
Thank you Fu.  Can you expand on what you mean by 'logical issue with LUKS'?
I don't believe there is anything wrong with the disks (one NVMe and one SSD...the NVMe has the main OS and data).

Another question:  When you say "open the container...Must know the passprhase to unlock the LUKS encrypted..."  is that in reference to the passphrase used to unlock the disks just after BIOS and before the OS login?

Just being overly cautious as I don't want to make a mistake and ruin my chances at access/recovery.

---

### Post by TheFu on 2020-03-11
Please don't pull 1 phrase from a paragraph and try to parse it.  The paragraph goes together and is about a specific topic and command. If there is a physical or logical problem, that's outside my notes.  

I don't know how your system is setup.  Those are my notes for my system. If they help, great! I use dm-crypt+LUKS.  That is the default for an ubuntu install when we select whole disk encryption.  It has NOTHING to do with HOME directory encryption or actually  any specific login/username on the system.

None of those commands, when run with the correct options for your system, will harm anything. They are not destructive. The order in the notes is the order needed.  If you don't understand something RTFM for more details.  That shouldn't need to be said.  Running commands without understanding them is a poor practice.

---

### Post by EuclideanCoffee on 2020-03-11
Logical relates to software likely. Software is made up of many conditional statements, which is what "logical" typically means in computing.

---

### Post by kingreagan41 on 2020-03-11
Thanks Fu.  That's why I'm asking and I appreciate your notes.  They are a good starting point for me to give it a run.  I've already gone through a lot of documentation on LUKS already and do understand your path on this.  It always helps to have friendly validation.

---

### Post by kingreagan41 on 2020-03-11
Understood...however, my unclear question was more around where the logic problem is indicated.  I've already found the answer...that logic problems in this case would be solely on the disk and not within the BIOS.  For me, the NVMe and SSD are both in tact and do not have issues.  I just wish I had a twin system to drop these into and fire everything up normally instead of having to d1ck around with a crippled loaner system.

---

### Post by EuclideanCoffee on 2020-03-12
No, the disk cannot produce a logical problem. The logical problem is to due with software, not hardware. The BIOS wouldn't be the answer here either because the BIOS isn't working here. The tech stack is hardware, drivers, and then software (logical). The software part is LUKS, which is encrypts the disk with logical statements called conditional statements, see predicate calculus in wiki. :)

[https://en.wikipedia.org/wiki/First-order_logic](https://en.wikipedia.org/wiki/First-order_logic)

---

### Post by TheFu on 2020-03-12
> **kingreagan41 said:**
> Understood...however, my unclear question was more around where the logic problem is indicated.  I've already found the answer...that logic problems in this case would be solely on the disk and not within the BIOS.  For me, the NVMe and SSD are both in tact and do not have issues.  I just wish I had a twin system to drop these into and fire everything up normally instead of having to d1ck around with a crippled loaner system.

With Linux, you might be able to pull the storage devices and connect them to another, different, system.  The main issue would be any proprietary GPU drivers.  Those would need to be disabled, but other than that, the system should boot.  The 2nd disk may or may not be mounted, but that could be fixed by modifying the /etc/fstab - probably.  The storage controller might be an issue. Can't tell until you try.

Or the disks could be connected to almost any other recent Ubuntu OS and mounted RW for any changes needed OR to pull the data from the disks.

---

