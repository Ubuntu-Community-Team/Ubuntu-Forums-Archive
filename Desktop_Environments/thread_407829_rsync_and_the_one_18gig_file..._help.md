---
title: "rsync and the one 18gig file... help"
date: 2007-04-12
forum: Desktop Environments
---

### Post by Underpants on 2007-04-12
I have rsync set up on two machines. It works great, with the exception of a full backup image that I need to move each day. It's about 18 gigs in size, I've not even mentioned the larger ones that I haven't touched yet.

Anyway, 

The damn thing just sits at "1 file to consider" below is my code... is this normal?



```

rsync -avzI --progress --delete-after -e ssh aaron@x.x.x.x:/home/aaron/data/gwikmail.tib /home/aaron/gwik/gwikmail.tib


```

---

### Post by Underpants on 2007-04-12
It's sitting here: 

```

aaron@boxen:~$ rsync -avvvI --progress --delete-after -e ssh aaron@x.x.x.x:/home/aaron/data/gwikmail.tib /home/aaron/gwik/gwikmail.tib
opening connection using ssh -l aaron x.x.x.x rsync --server --sender -vvvlogDtprI . /home/aaron/data/gwikmail.tib
aaron@x.x.x.x's password:
receiving file list ...
server_sender starting pid=6966
[sender] make_file(gwikmail.tib,*,2)
recv_file_name(gwikmail.tib)
received 1 names
1 file to consider
recv_file_list done
get_local_name count=1 /home/aaron/gwik/gwikmail.tib
recv_files(1) starting
send_file_list done
send_files starting
generator starting pid=5270 count=1
delta-transmission enabled
recv_generator(gwikmail.tib,0)
generating and sending sums for 0
count=137389 rem=33056 blength=137384 s2length=4 flength=18874946048
send_files(0, /home/aaron/data/gwikmail.tib)


```

---

