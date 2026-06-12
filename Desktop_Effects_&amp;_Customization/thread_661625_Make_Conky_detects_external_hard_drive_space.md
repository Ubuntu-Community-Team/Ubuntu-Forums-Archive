---
title: "Make Conky detects external hard drive space"
date: 2008-01-08
forum: Desktop Effects &amp; Customization
---

### Post by CypherHackz on 2008-01-08
Hi,

I have two hard drives. One is run Ubuntu and one is for Windows. My Conky config can detect the Ubuntu drive space correctly.

But how I can make it to check and detect my Windows hard drive (which has 3 parttions)? And then make it to display the hard drive space on the desktop?

Thank you.

---

### Post by rrr0321 on 2008-01-08
Assuming you can view your Windows partitions in Ubuntu File Browser go to your file system  /Media folder and open it up. Note the names of your partitions in this folder. I only have 1 partition for XP Pro and 1 for Ubuntu and the lines I added to conkyrc are:

${color white}Disk Partitions:
${color white}Ubuntu:  /home ${color white}${fs_used /home}/${fs_size /home} ${fs_free_perc /home}% ${color white}free)
${color white}Windows XP:  ${color white}${fs_used /media/Windows XP Pro}${color white}/${color white}${fs_size /media/Windows XP Pro} ${color white}(${color white}${fs_free /media/Windows XP Pro}, ${fs_free_perc /media/Windows XP Pro}% ${color white}free)

After /media change the names to your partition names in the above lines. If you have 3 partitions you will need to insert the lines 3 times to get what you are looking for. I also attach a screenshot of what my Conky looks like. I hope this helps you out!

---

### Post by CypherHackz on 2008-01-09
thanks for the response. but it is not for my case. 

as i said in my post, i have two hard drives. what i want is, to detect the another hard drive partitions and not the partitions in the same hard drive where i install ubuntu. :)

let makes it clear.

HD1: Partition 1: Ubuntu; Partition 2: Download;  Partition 3: Movies
HD2: Partition 1: Windows; Partition 2: My Files; Partition 3: Program Files

So, what I want is to detect the partitions in HD2 and not in HD1. I already success in detect the partitions in HD1. Only HD2 still no success.

Again, thanks. :)

---

