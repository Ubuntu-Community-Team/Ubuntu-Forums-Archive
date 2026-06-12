---
title: "Moving &quot;Completely&quot; to Ext4"
date: 2009-05-10
forum: General Help
---

### Post by shafin on 2009-05-10
I just used the tunetofs command from a liveCD to start mounting my system as ext4, and the result has been almost no visible change in boot time. Jaunty with ext3 knocked 5 secs off my boot time with intrepid. I'm thinking maybe because the data is still structured in ext3, there is no change. Now the question is, if I boot from a liveCD and move all the data ou of my '/' partition to another ext4 partition, and move them back in, will they be written in proper ext4 structure, or will they remain in current ext3 structure? Also will there be any permission problems? I have a seperate home partition, and will not move the data from that partition.

Have any of you done it?

---

### Post by danwood76 on 2009-05-10
You can use the tar backup method to move the files off the ext3 partition and retain permissions. (google tar backup ubuntu)
If you then untar to ext4 it should create all the files in the new structure.

---

### Post by shafin on 2009-05-10
Thanks. I will try it as soon as I can find some spare time. Will report the results then.

---

