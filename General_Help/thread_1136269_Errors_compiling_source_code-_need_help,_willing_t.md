---
title: "Errors compiling source code- need help, willing to pay someone!"
date: 2009-04-24
forum: General Help
---

### Post by gareth40 on 2009-04-24
First of all im new to these forums, sorry if ive posted this in the wrong category.
 
Im wanitng to run a chess server using the FICS sourcecode from [ftp.freechess.org]("ftp://ftp.freechess.org"), the package im trying to compile is "FICS.1.6.2.tar.gz" its on the freechess.org ftp server under pub/unix, however im getting the following errors:
 
This is on ubuntu desktop, im not a programmer and im only following the instructions that came with the FICS package, I have successfully compiled other packages like irc servers etc and had them working but this chess server is just being stubborn. I wouldnt a clue what to do, as I am no programmer.
 
If someone could help me get this up and running I would be willing to pay them for whatever it takes.
 
```

[FONT=Courier New][SIZE=2]ubuntu@ubuntu:~/Desktop/FICS.DIST/FICS$ makedepend[/SIZE][/FONT]
[SIZE=2][FONT=Courier New]ubuntu@ubuntu:~/Desktop/FICS.DIST/FICS$ make[/FONT][/SIZE]
[SIZE=2][FONT=Courier New]cc ficsmain.o  network.o lists.o formula.o playerdb.o command.o talkproc.o comproc.o matchproc.o movecheck.o ratings.o gamedb.o channel.o utils.o rmalloc.o legal.o vers.o variable.o board.o gameproc.o algcheck.o adminproc.o multicol.o eco.o rating_conv.o shutdown.o obsproc.o   -o fics[/FONT][/SIZE]
[SIZE=2][FONT=Courier New]command.o: In function `process_password':[/FONT][/SIZE]
[SIZE=2][FONT=Courier New]/home/ubuntu/Desktop/FICS.DIST/FICS/command.c:646: undefined reference to `crypt'[/FONT][/SIZE]
[SIZE=2][FONT=Courier New]comproc.o: In function `com_password':[/FONT][/SIZE]
[SIZE=2][FONT=Courier New]/home/ubuntu/Desktop/FICS.DIST/FICS/comproc.c:458: undefined reference to `crypt'[/FONT][/SIZE]
[SIZE=2][FONT=Courier New]/home/ubuntu/Desktop/FICS.DIST/FICS/comproc.c:468: undefined reference to `crypt'[/FONT][/SIZE]
[SIZE=2][FONT=Courier New]comproc.o: In function `com_who':[/FONT][/SIZE]
[SIZE=2][FONT=Courier New]/home/ubuntu/Desktop/FICS.DIST/FICS/comproc.c:1109: undefined reference to `floor'[/FONT][/SIZE]
[SIZE=2][FONT=Courier New]/home/ubuntu/Desktop/FICS.DIST/FICS/comproc.c:1110: undefined reference to `ceil'[/FONT][/SIZE]
[SIZE=2][FONT=Courier New]ratings.o: In function `rating_add':[/FONT][/SIZE]
[SIZE=2][FONT=Courier New]/home/ubuntu/Desktop/FICS.DIST/FICS/ratings.c:113: undefined reference to `sqrt'[/FONT][/SIZE]
[SIZE=2][FONT=Courier New]/home/ubuntu/Desktop/FICS.DIST/FICS/ratings.c:125: undefined reference to `sqrt'[/FONT][/SIZE]
[SIZE=2][FONT=Courier New]/home/ubuntu/Desktop/FICS.DIST/FICS/ratings.c:137: undefined reference to `sqrt'[/FONT][/SIZE]
[SIZE=2][FONT=Courier New]/home/ubuntu/Desktop/FICS.DIST/FICS/ratings.c:151: undefined reference to `sqrt'[/FONT][/SIZE]
[SIZE=2][FONT=Courier New]ratings.o: In function `rating_remove':[/FONT][/SIZE]
[SIZE=2][FONT=Courier New]/home/ubuntu/Desktop/FICS.DIST/FICS/ratings.c:183: undefined reference to `sqrt'[/FONT][/SIZE]
[SIZE=2][FONT=Courier New]ratings.o:/home/ubuntu/Desktop/FICS.DIST/FICS/ratings.c:207: more undefined references to `sqrt' follow[/FONT][/SIZE]
[SIZE=2][FONT=Courier New]ratings.o: In function `GE':[/FONT][/SIZE]
[SIZE=2][FONT=Courier New]/home/ubuntu/Desktop/FICS.DIST/FICS/ratings.c:586: undefined reference to `pow'[/FONT][/SIZE]
[SIZE=2][FONT=Courier New]ratings.o: In function `current_sterr':[/FONT][/SIZE]
[SIZE=2][FONT=Courier New]/home/ubuntu/Desktop/FICS.DIST/FICS/ratings.c:593: undefined reference to `log'[/FONT][/SIZE]
[SIZE=2][FONT=Courier New]/home/ubuntu/Desktop/FICS.DIST/FICS/ratings.c:593: undefined reference to `sqrt'[/FONT][/SIZE]
[SIZE=2][FONT=Courier New]ratings.o: In function `rating_sterr_delta':[/FONT][/SIZE]
[SIZE=2][FONT=Courier New]/home/ubuntu/Desktop/FICS.DIST/FICS/ratings.c:680: undefined reference to `sqrt'[/FONT][/SIZE]
[SIZE=2][FONT=Courier New]adminproc.o: In function `com_addplayer':[/FONT][/SIZE]
[SIZE=2][FONT=Courier New]/home/ubuntu/Desktop/FICS.DIST/FICS/adminproc.c:841: undefined reference to `crypt'[/FONT][/SIZE]
[SIZE=2][FONT=Courier New]adminproc.o: In function `com_asetpasswd':[/FONT][/SIZE]
[SIZE=2][FONT=Courier New]/home/ubuntu/Desktop/FICS.DIST/FICS/adminproc.c:1054: undefined reference to `crypt'[/FONT][/SIZE]
[SIZE=2][FONT=Courier New]collect2: ld returned 1 exit status[/FONT][/SIZE]
[SIZE=2][FONT=Courier New]make: *** [fics] Error 1[/FONT][/SIZE]
[SIZE=2][FONT=Courier New]ubuntu@ubuntu:~/Desktop/FICS.DIST/FICS$ /home/ubuntu/Desktop[/FONT][/SIZE]
 

```

---

