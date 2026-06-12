---
title: "Partition Recovery... Urgent Help Needed."
date: 2006-06-27
forum: Desktop Environments
---

### Post by Janissary on 2006-06-27
Hi,

I did something stupid today...

I was using "**shred -x -v -n 0 -z /dev/hda**" on my desktop computer with a live cd. when I type command it says are you sure etc.

Then I wondered what will the warning message in Ubuntu like? 

I typed shred -x -v -n 0 -z /dev/hda in my notebook than
whaaaa
the process started... I immediately hit ctrl+c and exited... check drives if something wrong... no everything was OK

than restarted computer after a while... an BUMB... no operating system no partiton in my hdd... it show as unallocated in partition magic

I need to recover my ext3 partitions what can I do?

thanks....

---

### Post by spyke01 on 2006-06-27
did a little something like that with bat command in windows, however i meant to do it. I believe the same principle applies to *nix systems however, basiclly the OS and info about drives is stored in memory, and written to disk at shutdown, this is also the basis of the Living Death virus(my favorite)

There are a few things you can try, i dont know if they will work though, get a backtrack linux cd(contains forensic tools to try and recover the partitions and information) and you can also try testdisk(do a google search).

I wish you luck, as i was in your shoes not too recently

---

