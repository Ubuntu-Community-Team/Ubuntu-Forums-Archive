---
title: "[SOLVED] How do I disable autologin - usermod -l knackered it up"
date: 2008-12-30
forum: Desktop Environments
---

### Post by theinnercityhippy on 2008-12-30
Hiya,

Spending the day repartitioning and streamlining my new acer aspire one.

I've created seperate partitions for /home and /boot and am installing an additional 2 OS's to go with the default Linpus Lite, each in their own prtitions using a shared /home (with seperate usernames to avoid confusion. I've successfully installed Ubuntu (which I have used for some time on my Primary system) and will be installing Backtrack next.

The problem I have is with the Linpus system which uses xfce4

To keep the computer consistent, I used the usermod commands to change the default username from "USER" to "jimdog-linpus". Now when I try to start this system it won't log in as the autologin is still set to USER which no longer exists, all I get is a blck screen with an x cursor for the mouse. Alt+F2 won't work to get a terminal nor any other command I can think of.

Ubuntu loads fine, this is what I'm using now.

Is there any files I can modify to either disable autologin and give me the option to login manually with my password, or change the username back again unil I can find a solution.

Just to clarify, I need to be able to do this directly to the mouned filesystem using Ubuntu as I can't log in to linpus

Many thanks, I've completely run out of ideas

-JimDog*-

---

### Post by theinnercityhippy on 2008-12-30
Ahaa!##

After a long days faff i have solved my own problem, posting a quick how to here for anyone else who has similar problem. Turns out the solution was with chroot, which is something I've been meaning to have a play with for a while now and this has given me the chance.

Firstly, I needed to check that the filesystem was mounted as it is on a seperate partition. Ubuntu being wonderful as it is did this for me automatically by clicking on the appropriate icon in nautilus and entering my password. If this doesn't happen automatically, you can do it by hand on the command line;

    :~$>sudo mkdir /mnt/linpus

To make a directory in which you can mount your filesystem

    :~$>mount -t ext2 /dev/sda5 /mnt/linpus

To tell it to mount the partition /dev/sda5 at that place/ the -t flag is essential and relates to the filesystem type, in this case ext2.

By issuing the command

    :~$>sudo chroot /media/linpus

I got a root shell in that directory, as if I was using a terminal from that operating system when booted. from which I could make the required changes.

    :~$>sudo usermod -l user jimdog-linpus

To change the username back again. However, by all my fannying around with the files, I ran into a different problem and couldn't log in as user. After lots of hair pulling out, I discovered that I had changed the write/read/execute permissions of my home folder. It is necessary for these to be set to be available only to the user and so it was back to the command line temporarily

    :~$>cd /home
    :~$>sudo chmod u+rwx
    :~$>sudo chmod g-rwx
    :~$>sudo chmod o-rwx

And lo and behold, my system works! If anyone has any better ideas to do this than these scribblings, or can expand on them to help other users who might run into similar problems then please feel free to add them as replies.

-JimDog*-

---

