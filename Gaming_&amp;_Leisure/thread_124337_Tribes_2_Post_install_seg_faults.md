---
title: "Tribes 2 Post install seg faults"
date: 2006-02-01
forum: Gaming &amp; Leisure
---

### Post by Endwin on 2006-02-01
Greetings,

I have a copy of tribes 2 linux. After installing it as root I ran the program and all it says is Segmentation Fault. Fine, so I tried downloading a patch and when it tries to apply it I get this:

endwin@navi:~$ sudo ./tribes2-25026-x86.run
Verifying archive integrity...OK
Uncompressing Tribes 2 25026 Update...........................................................................................................
./update.sh: line 60: 13835 Segmentation fault      loki_patch --verify patch.dat
The program returned an error code (1)
endwin@navi:~$

Ok I think, so lets try this through trying to go on-line with it's updater and there it fails as well  in the error output I get

Looking up sunsite.dk
Connecting to sunsite.dk
Connected
Transfer complete
Calculating MD5 checksum
Verification succeeded
Ready for update
Performing update
Update: /home/endwin/.loki/loki_update/tmp/tribes2-25034-cdrom-x86.run
Unpacking archive
Verifying archive integrity...OK
Uncompressing Tribes 2 25034 Update................................................................................................................................
./update.sh: line 60: 13615 Segmentation fault      loki_patch --verify patch.dat
The program returned an error code (1)
Update failed

I have tried this as a user, root, while in the sh shell as root, and a user, and I keep getting the same error.

Any ideas on how to solve this one?

---

