---
title: "Need access to an AFP volume through ubuntu"
date: 2006-03-01
forum: Desktop Environments
---

### Post by ponkan on 2006-03-01
The situation is, I'm using ubuntu in a college that uses mac servers. I would like to be able to work on both systems without having to ftp files anytime I move between my apartment and the school. Our mac home directories are exported under afp.

I did a search, but only came up with how to share files *from* linux/unix to mac on an afp interface, like through netatalk, while I'm looking to mount the afp volume on my ubuntu machine.

Any help, hints, leads, or advice on the matter would be greatly appreciated.

---

### Post by ponkan on 2006-03-13
Anybody at all with any information/experience?

---

### Post by JanvL on 2006-03-13
I guess this is the link you were looking for:

[http://www.anders.com/projects/netatalk/](http://www.anders.com/projects/netatalk/)

lots of fun, jan

---

### Post by JanvL on 2006-03-13
one more

[http://ubuntuforums.org/showpost.php?p=813001](http://ubuntuforums.org/showpost.php?p=813001)

postcount=3 from AZ

there the packages you need are listed

---

### Post by wesman83 on 2006-06-11
the netatalk site is way out of date and the afpfs doesnt work in the newer kernels... has anyone figured this out?

---

### Post by christhemonkey on 2006-06-11
open-afs client?
```
sudo apt-get install openafs-client
```

---

### Post by Hiram on 2007-02-17
well the only option atm is to use the fuse-based afpfs-ng, (its on the list of fuse-based filesystems on the fuse site) however i didn't manage to get it compiled,

---

### Post by alexthepuffin on 2007-03-07
I wrote afpfs-ng.  What compilation problems were you having and what version was this?  I'd like to fix them.

- Alex

---

### Post by Hiram on 2007-03-08
> **alexthepuffin said:**
> I wrote afpfs-ng.  What compilation problems were you having and what version was this?  I'd like to fix them.

- Alex

well i suspect that it is a ubuntu specific problem since i used it before without problems on a gentoo installation

but on ubuntu i get :

commands.c:8:18: error: fuse.h: No such file or directory
commands.c:9:27: error: fuse/fuse_opt.h: No such file or directory
commands.c: In function ‘start_fuse_thread’:
commands.c:145: warning: implicit declaration of function ‘get_debug_mode’
commands.c:160: warning: passing argument 2 of ‘afp_register_fuse’ from incompatible pointer type
commands.c: In function ‘process_mount’:
commands.c:635: warning: passing argument 3 of ‘new_server’ from incompatible pointer type
make[1]: *** [afpfsd-commands.o] Error 1

which makes no sense since fuse.h is in my /usr/include/linux dir...

I'm am running feisty on amd64, maybe that that is the problem. however it would be really nice if you could distribute .deb packages also next to the source and rpm's

---

### Post by alexthepuffin on 2007-03-10
Do you have the development libraries installed?  They should be in /usr/include/fuse.  I'm sure there's an ubuntu package for them.

BTW, if anyone has an Ubuntu package for afpfs-ng, I'd really appreciate it.  It would make afpfs-ng much easier to install for Ubuntu users.

- Alex

---

### Post by alexthepuffin on 2007-03-10
Some clarifications for people new to AFP.

AFP is the Apple Filing Protocol, used to share files over a network (AppleTalk or TCP) generally between macs.

netatalk is an opensource *server*

There have been several AFP clients, afpfs-ng is the only modern, open source one.

AFS is the Andrew File System, this is totally different and has nothing to do with AFP.

---

### Post by Hiram on 2007-03-11
> **alexthepuffin said:**
> Do you have the development libraries installed?  They should be in /usr/include/fuse.  I'm sure there's an ubuntu package for them.

BTW, if anyone has an Ubuntu package for afpfs-ng, I'd really appreciate it.  It would make afpfs-ng much easier to install for Ubuntu users.

- Alex

ah i found it, apparently the called the devel files libfuse-dev instead of fuse-dev as one might expect (since fuse is called fuse). one also need the libgmp3-dev package but with those it compiles. i'm looking into creating a .deb as soon as i know how.

however it still doesn't work for me.

what i try to do is access volumes on a server over the internet and to do that i need to open a ssh tunnel. one of the things i noticed is that you cannot specify a port in afpfs-ng which is very inconvenient since ssh tunneling of 548 is restricted for root only.

however i got it to work as far that i could connect and got this message:

The afpfs daemon does not appear to be running, let me start it for you
mounting Persoonlijke Website on afp
Starting mount.
Creating new connection to server
Actually mounting.
Volume Persoonlijke Website does not exist on server.
Choose from:
   Users
   General

well that seemed to work so i changed the name of the volume and it seemed to mount ok, but when i tried to use it i got:
ls: afp: Input/output error

so currently i'm stuck there.

i noticed another thing however; since i was working as root (using sudo) mounted it as root and thus had not the right permissions to access the folder as a user. could it be possible to give afpfs-ng similar options as other (fuse based) filesystems for example options to specify an uid and gid?

---

### Post by alexthepuffin on 2007-03-11
Hiram,

Yes, I'll work on setting up the uid/gid feature at some point.  It's on the list.

There's a user mapping feature in the code that isn't complete.  

For the port problem, attached is a patch that will let you use '-o portnum' with your mount command.  Unzip and apply the patch, rebuild and then you should have it.  I just put it into CVS also.

What would help me in debugging the situation is if you could kill off afpfsd, then run:
afpfsd -d

and then run your afp_client command again.

Laat me even weten waneer je een .deb hebt gemaakt.

I realize that afpfs-ng is still young; I'm trying to get users to try it so that I can increase the quality of it.


- Alex

---

### Post by Hiram on 2007-03-11
> **alexthepuffin said:**
> Hiram,

Yes, I'll work on setting up the uid/gid feature at some point.  It's on the list.

There's a user mapping feature in the code that isn't complete.  

For the port problem, attached is a patch that will let you use '-o portnum' with your mount command.  Unzip and apply the patch, rebuild and then you should have it.  I just put it into CVS also.

What would help me in debugging the situation is if you could kill off afpfsd, then run:
afpfsd -d

and then run your afp_client command again.

Laat me even weten waneer je een .deb hebt gemaakt.

I realize that afpfs-ng is still young; I'm trying to get users to try it so that I can increase the quality of it.


- Alex
tnx for the portnumber option

 
well i did what you asked and after doing 
hiram@hermes:~$ /usr/local/bin/afp_client mount -o 10548 localhost:paassen afp
mounting paassen on afp
Starting mount.
Creating new connection to server
Actually mounting.
Mounting succeeded.
hiram@hermes:~$ ls afp
ls: afp: Input/output error

i got this  :

Starting up AFPFS version 0.4
Got connection 4
mounting paassen on afp
Got a signal 12
Got a server signal, 0
Got a signal 12
Got a server signal, 0
Got a signal 12
Got a server signal, 0
Removing connection for server Fourier
Got a signal 12
Got a server signal, 0
Starting mount.
Creating new connection to server
Got a signal 12
Got a server signal, 0
Actually mounting.
unique: 1, opcode: INIT (26), nodeid: 0, insize: 56
INIT: 7.8
flags=0x00000003
max_readahead=0x00020000
Mounting succeeded.
Got a signal 12
Got a server signal, 0
   INIT: 7.8
   flags=0x00000001
   max_readahead=0x00020000
   max_write=0x00020000
   unique: 1, error: 0 (Success), outsize: 40
unique: 2, opcode: GETATTR (3), nodeid: 1, insize: 40
   unique: 2, error: -5 (Input/output error), outsize: 16
unique: 3, opcode: ACCESS (34), nodeid: 1, insize: 48
ACCESS / 04
   unique: 3, error: -38 (Function not implemented), outsize: 16
unique: 4, opcode: GETATTR (3), nodeid: 1, insize: 40
   unique: 4, error: -5 (Input/output error), outsize: 16


about the deb file.. i actualy got a working .deb but its binairy so it only works on ubuntu feisty amd64, but i will try to make an source .deb

---

### Post by alexthepuffin on 2007-03-11
After you do a mount, what's the output of:
afp_client status

Also, did the patch apply for you correctly?

- A

---

### Post by Hiram on 2007-03-11
> **alexthepuffin said:**
> After you do a mount, what's the output of:
afp_client status

Also, did the patch apply for you correctly?

- A

AFPFS Version: 0.4
Server Fourier
    connection: 127.0.0.1:10548 (active)
    AFP version: AFP3.2
    using UAM: DHX2
    login message:
    type: Macintosh
    signature:
    transmit delay: 0ms
    quantums: 262144(tx) 131072(rx)
    last request id: 242 in queue: 0
    transfer: 7257(rx) 5176(tx)
    runt packets: 0
    Volume Users, id 0, attribs 0x0 mounted: No

    Volume General, id 0, attribs 0x0 mounted: No

    Volume paassen, id 1, attribs 0x46c mounted: afp
        did cache stats: 0 miss, 0 hit, 0 expired, 0 force removal


yes the patch applied correctly

i also included my attempt to make a .deb for afpfs-ng 
it must warn however that although it is a valid. deb is is made on ubuntu feisty and thus might not work on other debian based systems.

i also tried to get the copyright stuff a bit right but i could have missed something so if i'm not mistaken one can recreate the .deb by unpacking the .orig.tar and applying the diff on it and then running dpkg-buildpackage -rfakeroot 

well see [http://www.debian.org/doc/manuals/maint-guide/index.en.html](http://www.debian.org/doc/manuals/maint-guide/index.en.html) for more info

the .orig.tar btw doesn't contain the same files as the tar from sourceforge, i had to replace the config.sub and config.guess symlinks with real files from my system to make the buildscript work and i applied the portnum patch on it




oh another thing i found was that when i tried to create a i386 package on another computer i got this :

fuse_int.c:2045:61: error: macro "fuse_main" passed 4 arguments, but takes just 3
fuse_int.c: In function &#8216;afp_register_fuse&#8217;:
fuse_int.c:2045: error: &#8216;fuse_main&#8217; undeclared (first use in this function)
fuse_int.c:2045: error: (Each undeclared identifier is reported only once
fuse_int.c:2045: error: for each function it appears in.)
make[1]: *** [afpfsd-fuse_int.o] Error 1

i got that from the source included but also from the source i got from sourceforge
that was on ubuntu edgy i386

---

### Post by alexthepuffin on 2007-03-11
Okay, a few more things:

- on the Mac side and on the Linux side, what are the permissions of the mount points?

- what happens when you do a 'df' ?

- do any of the other volumes work properly?

For more debugging, could you try getting a network packet dump?  You'd do that with something like:
tcpdump -i eth0 -s 0 -w mycapture port 10548

... or use wireshark/ethereal.

Your password won't be in the trace since you're using DHX2.

- Alex

---

### Post by Hiram on 2007-03-11
> **alexthepuffin said:**
> Okay, a few more things:

- on the Mac side and on the Linux side, what are the permissions of the mount points?

- what happens when you do a 'df' ?

- do any of the other volumes work properly?

For more debugging, could you try getting a network packet dump?  You'd do that with something like:
tcpdump -i eth0 -s 0 -w mycapture port 10548

... or use wireshark/ethereal.

Your password won't be in the trace since you're using DHX2.

- Alex
as far as i know i got read/write permissions on both sides


wow thats surprising, df actualy works 
$df
Fourier:paassen       1.1T 1019G   18G  99% /home/hiram/afp
afpfsd -d:
unique: 5, opcode: STATFS (17), nodeid: 1, insize: 40
   unique: 5, error: 0 (Success), outsize: 96

trying to go into a subdir which does exist however still give the iput output error
unique: 7, opcode: GETATTR (3), nodeid: 1, insize: 40
   unique: 7, error: -5 (Input/output error), outsize: 16
unique: 8, opcode: LOOKUP (1), nodeid: 1, insize: 50
LOOKUP /Documents
   unique: 8, error: -5 (Input/output error), outsize: 16

trying to go in a dir which doesnt exist gives an file not found error 


i will try to get a tcpdump of some sort however wireshark probably won't work unless you got a way to decrypt the ssh packages. since the afp mount isn't visible from the internet i got to use an ssh tunnel to get there.

hehe starting to look like slowchat here :)

---

### Post by alexthepuffin on 2007-03-11
If you're trying to get a tcpdump, you should be able to do that by grabbing the traffic in the loopback.  Eg.

tcpdump -i lo ...

Also, could you add "#define LOG_FUSE_EVENTS 1" to the top of fuse_int.c, rebuild and give me the log?

And, could you try this on another volume?

- Alex

---

### Post by Hiram on 2007-03-12
> **alexthepuffin said:**
> If you're trying to get a tcpdump, you should be able to do that by grabbing the traffic in the loopback.  Eg.

tcpdump -i lo ...

done, attached> 

Also, could you add "#define LOG_FUSE_EVENTS 1" to the top of fuse_int.c, rebuild and give me the log?
done, but where can i find the log?> 

And, could you try this on another volume?

- Alex

did that already, gives the same errors.

---

### Post by dennis1200 on 2007-03-12
I just came across this - looks awesome. However, I hit some compile issues on Edgy i386 involving fuse. I have libfuse-dev and libgmp3-dev installed as mentioned earlier, but this is what I get on 'sudo make install':

```
/usr/include/fuse/fuse.h:20:1: warning: this is the location of the previous definition
daemon.c: In function ‘deal_with_server_signals’:
daemon.c:164: warning: passing argument 3 of ‘pthread_create’ from incompatible pointer type
daemon.c: In function ‘main’:
daemon.c:405: warning: control reaches end of non-void function
if gcc -DHAVE_CONFIG_H -I. -I. -I.    -g -Wall -D_FILE_OFFSET_BITS=64  -g -O2 -MT afpfsd-fuse_int.o -MD -MP -MF ".deps/afpfsd-fuse_int.Tpo" -c -o afpfsd-fuse_int.o `test -f 'fuse_int.c' || echo './'`fuse_int.c; \
        then mv -f ".deps/afpfsd-fuse_int.Tpo" ".deps/afpfsd-fuse_int.Po"; else rm -f ".deps/afpfsd-fuse_int.Tpo"; exit 1; fi
fuse_int.c: In function ‘afp_getattr’:
fuse_int.c:206: warning: passing argument 2 of ‘apple_translate’ discards qualifiers from pointer target type
fuse_int.c: In function ‘afp_rmdir’:
fuse_int.c:434: warning: passing argument 2 of ‘apple_translate’ discards qualifiers from pointer target type
fuse_int.c: In function ‘afp_unlink’:
fuse_int.c:494: warning: passing argument 2 of ‘apple_translate’ discards qualifiers from pointer target type
fuse_int.c: In function ‘afp_readdir’:
fuse_int.c:560: warning: passing argument 2 of ‘apple_translate’ discards qualifiers from pointer target type
fuse_int.c: In function ‘afp_mknod’:
fuse_int.c:678: warning: passing argument 2 of ‘apple_translate’ discards qualifiers from pointer target type
fuse_int.c: In function ‘afp_release’:
fuse_int.c:748: warning: cast to pointer from integer of different size
fuse_int.c:767: warning: cast to pointer from integer of different size
fuse_int.c:796: warning: cast to pointer from integer of different size
fuse_int.c: In function ‘afp_open’:
fuse_int.c:823: warning: assignment makes integer from pointer without a cast
fuse_int.c:837: warning: passing argument 2 of ‘apple_translate’ discards qualifiers from pointer target type
fuse_int.c: In function ‘afp_write’:
fuse_int.c:1065: warning: cast to pointer from integer of different size
fuse_int.c:1086: warning: passing argument 2 of ‘apple_translate’ discards qualifiers from pointer target type
fuse_int.c:1090: warning: implicit declaration of function ‘volinfo_write’
fuse_int.c: In function ‘afp_read’:
fuse_int.c:1282: warning: cast to pointer from integer of different size
fuse_int.c:1290: warning: passing argument 2 of ‘apple_translate’ discards qualifiers from pointer target type
fuse_int.c: In function ‘afp_truncate’:
fuse_int.c:1466: warning: passing argument 2 of ‘apple_translate’ discards qualifiers from pointer target type
fuse_int.c:1478: warning: cast to pointer from integer of different size
fuse_int.c: At top level:
fuse_int.c:2033: warning: initialization from incompatible pointer type
fuse_int.c:2045:61: error: macro "fuse_main" passed 4 arguments, but takes just 3
fuse_int.c: In function ‘afp_register_fuse’:
fuse_int.c:2045: error: ‘fuse_main’ undeclared (first use in this function)
fuse_int.c:2045: error: (Each undeclared identifier is reported only once
fuse_int.c:2045: error: for each function it appears in.)
make: *** [afpfsd-fuse_int.o] Error 1

```

---

### Post by Hiram on 2007-03-12
> **dennis1200 said:**
> I just came across this - looks awesome. However, I hit some compile issues on Edgy i386 involving fuse. I have libfuse-dev and libgmp3-dev installed as mentioned earlier, but this is what I get on 'sudo make install':
....


yeah that was exactly the same what i was getting

---

### Post by alexthepuffin on 2007-03-12
What version of fuse are in feisty and edgy?  This will be why there are compilation failures.

-  Alex

---

### Post by alexthepuffin on 2007-03-12
> **Hiram said:**
> done, attacheddone, but where can i find the log?

did that already, gives the same errors.

It'll put the errors in with the rest of the log, you can see them since they start with "*** ".

The problem here is with the mapping of users between client and server.  I suspect the attached patch will be able to help this, let me know.

For future testing, can you give me the username and uid on both the client and server?  I'll test that combination before the next release.

---

### Post by Hiram on 2007-03-12
> **alexthepuffin said:**
> What version of fuse are in feisty and edgy?  This will be why there are compilation failures.

-  Alex

feisty got libfuse.so.2.6.2
edgy got  libfuse.so.2.5.3

ow wow your patch fixed it for me!

local:
username = hiram
uid = 1000

this is from one server, i dont know the uid from the other since i got no ssh access to that one.
remote:
username = paassen
uid = 5428

ow and another thing i noticed is that the relative pad i give as a mount point is relative to the home dir and not to the current dir

so "afp_client mount server:vol afp" mounts on ~/afp instead of ./afp

---

### Post by alexthepuffin on 2007-03-12
> **Hiram said:**
> feisty got libfuse.so.2.6.2
edgy got  libfuse.so.2.5.3


Okay, I'll make sure that I test on both for the next release.  If someone using either one of those wants to give me a patch, I'll include it.

> **Hiram said:**
> 
ow wow your patch fixed it for me!


Cool.  The larger problem here is when both the username and the uid are mismatched.  I'll make it so that you can force the mapping to always be local.

I'll file a bug about the relative path problem.  It might be something like it mounts it relative to where you ran afpfsd, not where you ran afp_client.  Easily fixed.

Thanks.

---

### Post by Hiram on 2007-03-12
> **alexthepuffin said:**
> Okay, I'll make sure that I test on both for the next release.  If someone using either one of those wants to give me a patch, I'll include it.



Cool.  The larger problem here is when both the username and the uid are mismatched.  I'll make it so that you can force the mapping to always be local.

I'll file a bug about the relative path problem.  It might be something like it mounts it relative to where you ran afpfsd, not where you ran afp_client.  Easily fixed.

Thanks.
it would be cool to if you make it so that you can specify the local uid and gui, that way you can for example mount as root and still allow users to use the filesystem

---

### Post by alexthepuffin on 2007-03-12
> **Hiram said:**
> it would be cool to if you make it so that you can specify the local uid and gui, that way you can for example mount as root and still allow users to use the filesystem

Yup.  I'll add something like:
--map=forcelocal --map-local-uid=5428 --map-local-gid=5429

to the afp_client mount command.

The one problem to this is that if there's a file on the remote server owned by uid 500, but you've forced a local uid of 5428, the file will appear to be owned by 5428 but you won't be able to write to it.

- Alex

---

### Post by dennis1200 on 2007-03-14
I tried applying the patch posted above, but I still get the gamut of error messages. All sorts of fuse_int.c things passing arguments and casting pointers and implicit declarations. I just did "patch -p1 <afpfs_ng-hackmap.diff"

Something else I should do instead?

---

### Post by Hiram on 2007-03-14
> **dennis1200 said:**
> I tried applying the patch posted above, but I still get the gamut of error messages. All sorts of fuse_int.c things passing arguments and casting pointers and implicit declarations. I just did "patch -p1 <afpfs_ng-hackmap.diff"

Something else I should do instead?

well that patch was for the problem i had which was very different from what you have.

but i got it to compile bij changing 

in fuse_int.c (all the way at the end, the last function)

```
int afp_register_fuse(int fuseargc, char *fuseargv[],struct afp_volume * vol)
{
        global_volume=vol;

#if FUSE_USE_VERSION < 26
        return fuse_main(fuseargc, fuseargv, &afp_oper);
#else
```

into


```
int afp_register_fuse(int fuseargc, char *fuseargv[],struct afp_volume * vol)
{
        global_volume=vol;

#if FUSE_USE_VERSION < 1000
        return fuse_main(fuseargc, fuseargv, &afp_oper);
#else
```

basically i forced it to use the first call to fuse_main instead of the second
i know that it is a dirty hack but it seems to work here (at least i compiles)

---

### Post by alexthepuffin on 2007-03-14
> **dennis1200 said:**
> I tried applying the patch posted above, but I still get the gamut of error messages. All sorts of fuse_int.c things passing arguments and casting pointers and implicit declarations. I just did "patch -p1 <afpfs_ng-hackmap.diff"

Something else I should do instead?

Note that you should only ever need hackmap if you have a situation where you have different usernames *AND* uids between the client and server.


Let me know if the problem you ahve isn't related to the FUSE_USE_VERSION problem, though.


- Alex

---

### Post by alexthepuffin on 2007-03-14
> **Hiram said:**
> 

basically i forced it to use the first call to fuse_main instead of the second
i know that it is a dirty hack but it seems to work here (at least i compiles)

What version of FUSE do you have that requires this patch?  I'll try and fix up configure.ac to detect it accordingly.

- A

---

### Post by LdrJagMan on 2007-03-21
ok ok ok... do you have a package of afpfs for dapper handy... or something that i can accomplish in the terminal that i dont have to learn how to compile...

---

### Post by alexthepuffin on 2007-03-24
Not me.  But if an Ubuntu user would create one, I'll certainly put it on the afpfs-ng download site.

- A

---

### Post by LdrJagMan on 2007-03-27
Yay some one finally responded... now my question is anyone out there know how to package this thing?

---

### Post by Hiram on 2007-03-27
> **LdrJagMan said:**
> Yay some one finally responded... now my question is anyone out there know how to package this thing?

i can only try to make a .deb for edgy-386 or feisty-amd64 but compiling is fairly easy

just make sure you got libfuse-dev, build-essential and libgmp3-dev installed
in a terminal do:

$ sudo apt-get install  libfuse-dev build-essential libgmp3-dev 

and then you need to unzip the src en and do 
in the folder where you unzipt the src
$ ./configure
$ make
$ sudo make install
and it will work

---

### Post by LdrJagMan on 2007-03-28
Ok. Ill see if i can get a compile of it... Alex I need your best source code so I can compile it... where can i get it?
and mind going into more detail on how the heck to do that second step and compile,,, it's only my 3rd week with linux

---

### Post by alexthepuffin on 2007-03-31
Okay, I've release 0.4.1 which includes the patches we've talked about here.

You can get it from [https://sourceforge.net/project/showfiles.php?group_id=179882](https://sourceforge.net/project/showfiles.php?group_id=179882)

For the novice, in order to build you should:
tar -xjf afpfs-ng-0.4.1.tar.bz2
cd afpfs-ng-0.4.1
./configure
make
sudo make install

Let me know if there are problems.  I'm especially curious if my fixes will let it compile on edgy, feisty and anything else you've got.


- Alex

---

### Post by LdrJagMan on 2007-04-02
Make what? i need $make: *** No targets specified and no makefile found.  Stop.
Help...
if i am using the right termanolgy i need an argument like -Whatever or --Blah or -bL or somthing

---

### Post by alexthepuffin on 2007-04-02
It's like you didn't do the ./configure step, or it failed for some reason.  Could you copy and paste what you saw on the console for the entire procedure?

Over time, this process will get easier for you.

- Alex

---

### Post by LdrJagMan on 2007-04-02
jagman@Dexlap:~/afpfs-ng-0.4.1$ ./configure
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... yes
checking for gcc... gcc
checking for C compiler default output file name... a.out
checking whether the C compiler works... yes
checking whether we are cross compiling... no
checking for suffix of executables...
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ANSI C... none needed
checking for style of include used by make... GNU
checking dependency style of gcc... gcc3
checking for a BSD-compatible install... /usr/bin/install -c
configure: error: cannot run /bin/sh ./config.sub
jagman@Dexlap:~/afpfs-ng-0.4.1$

thats the log from runnin ./configure

---

### Post by alexthepuffin on 2007-04-02
I think you're missing some things on your host which are causing it to not compile.

I'm not exactly sure what, but I'd do:

sudo apt-get instal libtool autoconf

anyway.  Let's start with that.

If that fails, I might try running 'autoreconf' before the configure.

- Alex

---

### Post by LdrJagMan on 2007-04-02
jagman@Dexlap:~/afpfs-ng-0.4.1$ ./configure
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... yes
checking for gcc... gcc
checking for C compiler default output file name... a.out
checking whether the C compiler works... yes
checking whether we are cross compiling... no
checking for suffix of executables...
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ANSI C... none needed
checking for style of include used by make... GNU
checking dependency style of gcc... gcc3
checking for a BSD-compatible install... /usr/bin/install -c
checking build system type... i686-pc-linux-gnu
checking host system type... i686-pc-linux-gnu
checking for a sed that does not truncate output... /bin/sed
checking for egrep... grep -E
checking for ld used by gcc... /usr/bin/ld
checking if the linker (/usr/bin/ld) is GNU ld... yes
checking for /usr/bin/ld option to reload object files... -r
checking for BSD-compatible nm... /usr/bin/nm -B
checking whether ln -s works... yes
checking how to recognise dependent libraries... pass_all
checking how to run the C preprocessor... gcc -E
checking for ANSI C header files... yes
checking for sys/types.h... yes
checking for sys/stat.h... yes
checking for stdlib.h... yes
checking for string.h... yes
checking for memory.h... yes
checking for strings.h... yes
checking for inttypes.h... yes
checking for stdint.h... yes
checking for unistd.h... yes
checking dlfcn.h usability... yes
checking dlfcn.h presence... yes
checking for dlfcn.h... yes
checking for g++... g++
checking whether we are using the GNU C++ compiler... yes
checking whether g++ accepts -g... yes
checking dependency style of g++... gcc3
checking how to run the C++ preprocessor... g++ -E
checking for g77... no
checking for f77... no
checking for xlf... no
checking for frt... no
checking for pgf77... no
checking for fort77... no
checking for fl32... no
checking for af77... no
checking for f90... no
checking for xlf90... no
checking for pgf90... no
checking for epcf90... no
checking for f95... no
checking for fort... no
checking for xlf95... no
checking for ifc... no
checking for efc... no
checking for pgf95... no
checking for lf95... no
checking for gfortran... no
checking whether we are using the GNU Fortran 77 compiler... no
checking whether  accepts -g... no
checking the maximum length of command line arguments... 32768
checking command to parse /usr/bin/nm -B output from gcc object... ok
checking for objdir... .libs
checking for ar... ar
checking for ranlib... ranlib
checking for strip... strip
checking if gcc supports -fno-rtti -fno-exceptions... no
checking for gcc option to produce PIC... -fPIC
checking if gcc PIC flag -fPIC works... yes
checking if gcc static flag -static works... yes
checking if gcc supports -c -o file.o... yes
checking whether the gcc linker (/usr/bin/ld) supports shared libraries... yes
checking whether -lc should be explicitly linked in... no
checking dynamic linker characteristics... GNU/Linux ld.so
checking how to hardcode library paths into programs... immediate
checking whether stripping libraries is possible... yes
checking if libtool supports shared libraries... yes
checking whether to build shared libraries... yes
checking whether to build static libraries... yes
configure: creating libtool
appending configuration tag "CXX" to libtool
checking for ld used by g++... /usr/bin/ld
checking if the linker (/usr/bin/ld) is GNU ld... yes
checking whether the g++ linker (/usr/bin/ld) supports shared libraries... yes
checking for g++ option to produce PIC... -fPIC
checking if g++ PIC flag -fPIC works... yes
checking if g++ static flag -static works... yes
checking if g++ supports -c -o file.o... yes
checking whether the g++ linker (/usr/bin/ld) supports shared libraries... yes
checking dynamic linker characteristics... GNU/Linux ld.so
checking how to hardcode library paths into programs... immediate
appending configuration tag "F77" to libtool
checking for main in -lfuse... yes
checking for main in -lncurses... no
checking for main in -lpthread... yes
checking for __gmpz_init in -lgmp... yes
checking for gcry_cipher_open in -lgcrypt... yes
checking for libgcrypt-config... /usr/bin/libgcrypt-config
checking for LIBGCRYPT - version >= 1.2.0... yes
checking LIBGCRYPT API version... okay
checking for ANSI C header files... (cached) yes
checking arpa/inet.h usability... yes
checking arpa/inet.h presence... yes
checking for arpa/inet.h... yes
checking fcntl.h usability... yes
checking fcntl.h presence... yes
checking for fcntl.h... yes
checking limits.h usability... yes
checking limits.h presence... yes
checking for limits.h... yes
checking netdb.h usability... yes
checking netdb.h presence... yes
checking for netdb.h... yes
checking stddef.h usability... yes
checking stddef.h presence... yes
checking for stddef.h... yes
checking for stdlib.h... (cached) yes
checking for string.h... (cached) yes
checking for strings.h... (cached) yes
checking sys/socket.h usability... yes
checking sys/socket.h presence... yes
checking for sys/socket.h... yes
checking sys/time.h usability... yes
checking sys/time.h presence... yes
checking for sys/time.h... yes
checking syslog.h usability... yes
checking syslog.h presence... yes
checking for syslog.h... yes
checking for unistd.h... (cached) yes
checking utime.h usability... yes
checking utime.h presence... yes
checking for utime.h... yes
checking for an ANSI C-conforming const... yes
checking for uid_t in sys/types.h... yes
checking for mode_t... yes
checking for off_t... yes
checking for size_t... yes
checking whether time.h and sys/time.h may both be included... yes
checking for pid_t... yes
checking for unistd.h... (cached) yes
checking vfork.h usability... no
checking vfork.h presence... no
checking for vfork.h... no
checking for fork... yes
checking for vfork... yes
checking for working fork... yes
checking for working vfork... (cached) yes
checking for stdlib.h... (cached) yes
checking for GNU libc compatible malloc... yes
checking sys/select.h usability... yes
checking sys/select.h presence... yes
checking for sys/select.h... yes
checking for sys/socket.h... (cached) yes
checking types of arguments for select... int,fd_set *,struct timeval *
checking for bzero... yes
checking for gethostbyname... yes
checking for gettimeofday... yes
checking for inet_ntoa... yes
checking for memset... yes
checking for select... yes
checking for socket... yes
checking for strchr... yes
checking for strerror... yes
checking for strstr... yes
checking for strtol... yes
configure: creating ./config.status
config.status: creating Makefile
config.status: creating config.h
config.status: config.h is unchanged
config.status: executing depfiles commands
jagman@Dexlap:~/afpfs-ng-0.4.1$ make
make  all-am
make[1]: Entering directory `/home/jagman/afpfs-ng-0.4.1'
if gcc -DHAVE_CONFIG_H -I. -I. -I.    -g -Wall -D_FILE_OFFSET_BITS=64  -g -O2 -MT afpfsd-commands.o -MD -MP -MF ".deps/afpfsd-commands.Tpo" -c -o afpfsd-commands.o `test -f 'commands.c' || echo './'`commands.c; \
        then mv -f ".deps/afpfsd-commands.Tpo" ".deps/afpfsd-commands.Po"; else rm -f ".deps/afpfsd-commands.Tpo"; exit 1; fi
commands.c:9:27: error: fuse/fuse_opt.h: No such file or directory
In file included from commands.c:25:
afp.h:11:1: warning: "FUSE_USE_VERSION" redefined
In file included from /usr/include/fuse/fuse.h:19,
                 from /usr/include/fuse.h:9,
                 from commands.c:8:
/usr/include/fuse/fuse_common.h:17:1: warning: this is the location of the previous definition
commands.c: In function ‘start_fuse_thread’:
commands.c:145: warning: implicit declaration of function ‘get_debug_mode’
commands.c:160: warning: passing argument 2 of ‘afp_register_fuse’ from incompatible pointer type
commands.c: In function ‘process_mount’:
commands.c:635: warning: passing argument 3 of ‘new_server’ from incompatible pointer type
make[1]: *** [afpfsd-commands.o] Error 1
make[1]: Leaving directory `/home/jagman/afpfs-ng-0.4.1'
make: *** [all] Error 2
jagman@Dexlap:~/afpfs-ng-0.4.1$ make
make  all-am
make[1]: Entering directory `/home/jagman/afpfs-ng-0.4.1'
if gcc -DHAVE_CONFIG_H -I. -I. -I.    -g -Wall -D_FILE_OFFSET_BITS=64  -g -O2 -MT afpfsd-commands.o -MD -MP -MF ".deps/afpfsd-commands.Tpo" -c -o afpfsd-commands.o `test -f 'commands.c' || echo './'`commands.c; \
        then mv -f ".deps/afpfsd-commands.Tpo" ".deps/afpfsd-commands.Po"; else rm -f ".deps/afpfsd-commands.Tpo"; exit 1; fi
commands.c:9:27: error: fuse/fuse_opt.h: No such file or directory
In file included from commands.c:25:
afp.h:11:1: warning: "FUSE_USE_VERSION" redefined
In file included from /usr/include/fuse/fuse.h:19,
                 from /usr/include/fuse.h:9,
                 from commands.c:8:
/usr/include/fuse/fuse_common.h:17:1: warning: this is the location of the previous definition
commands.c: In function ‘start_fuse_thread’:
commands.c:145: warning: implicit declaration of function ‘get_debug_mode’
commands.c:160: warning: passing argument 2 of ‘afp_register_fuse’ from incompatible pointer type
commands.c: In function ‘process_mount’:
commands.c:635: warning: passing argument 3 of ‘new_server’ from incompatible pointer type
make[1]: *** [afpfsd-commands.o] Error 1
make[1]: Leaving directory `/home/jagman/afpfs-ng-0.4.1'
make: *** [all] Error 2
jagman@Dexlap:~/afpfs-ng-0.4.1$ sudo make install
if gcc -DHAVE_CONFIG_H -I. -I. -I.    -g -Wall -D_FILE_OFFSET_BITS=64  -g -O2 -MT afpfsd-commands.o -MD -MP -MF ".deps/afpfsd-commands.Tpo" -c -o afpfsd-commands.o `test -f 'commands.c' || echo './'`commands.c; \
        then mv -f ".deps/afpfsd-commands.Tpo" ".deps/afpfsd-commands.Po"; else rm -f ".deps/afpfsd-commands.Tpo"; exit 1; fi
commands.c:9:27: error: fuse/fuse_opt.h: No such file or directory
In file included from commands.c:25:
afp.h:11:1: warning: "FUSE_USE_VERSION" redefined
In file included from /usr/include/fuse/fuse.h:19,
                 from /usr/include/fuse.h:9,
                 from commands.c:8:
/usr/include/fuse/fuse_common.h:17:1: warning: this is the location of the previous definition
commands.c: In function ‘start_fuse_thread’:
commands.c:145: warning: implicit declaration of function ‘get_debug_mode’
commands.c:160: warning: passing argument 2 of ‘afp_register_fuse’ from incompatible pointer type
commands.c: In function ‘process_mount’:
commands.c:635: warning: passing argument 3 of ‘new_server’ from incompatible pointer type
make: *** [afpfsd-commands.o] Error 1
jagman@Dexlap:~/afpfs-ng-0.4.1$

that is the last three things that i did and it still dident work... drat.... NEXT BRIGHT IDEA!

---

### Post by alexthepuffin on 2007-04-02
This was covered earlier.  You're missing the fuse devel libraries.  You can install them with:

sudo yum install libfuse-dev

Then continue with your configure.

You're getting there.

- Alex

---

### Post by LdrJagMan on 2007-04-02
sudo: yum: command not found :lolflag:

---

### Post by alexthepuffin on 2007-04-02
sorry. 

sudo apt-get install libfuse-dev

I'm not an ubuntu user.

- Alex

---

### Post by LdrJagMan on 2007-04-02
jagman@Dexlap:~/afpfs-ng-0.4.1$ ./configure
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... yes
checking for gcc... gcc
checking for C compiler default output file name... a.out
checking whether the C compiler works... yes
checking whether we are cross compiling... no
checking for suffix of executables...
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ANSI C... none needed
checking for style of include used by make... GNU
checking dependency style of gcc... gcc3
checking for a BSD-compatible install... /usr/bin/install -c
checking build system type... i686-pc-linux-gnu
checking host system type... i686-pc-linux-gnu
checking for a sed that does not truncate output... /bin/sed
checking for egrep... grep -E
checking for ld used by gcc... /usr/bin/ld
checking if the linker (/usr/bin/ld) is GNU ld... yes
checking for /usr/bin/ld option to reload object files... -r
checking for BSD-compatible nm... /usr/bin/nm -B
checking whether ln -s works... yes
checking how to recognise dependent libraries... pass_all
checking how to run the C preprocessor... gcc -E
checking for ANSI C header files... yes
checking for sys/types.h... yes
checking for sys/stat.h... yes
checking for stdlib.h... yes
checking for string.h... yes
checking for memory.h... yes
checking for strings.h... yes
checking for inttypes.h... yes
checking for stdint.h... yes
checking for unistd.h... yes
checking dlfcn.h usability... yes
checking dlfcn.h presence... yes
checking for dlfcn.h... yes
checking for g++... g++
checking whether we are using the GNU C++ compiler... yes
checking whether g++ accepts -g... yes
checking dependency style of g++... gcc3
checking how to run the C++ preprocessor... g++ -E
checking for g77... no
checking for f77... no
checking for xlf... no
checking for frt... no
checking for pgf77... no
checking for fort77... no
checking for fl32... no
checking for af77... no
checking for f90... no
checking for xlf90... no
checking for pgf90... no
checking for epcf90... no
checking for f95... no
checking for fort... no
checking for xlf95... no
checking for ifc... no
checking for efc... no
checking for pgf95... no
checking for lf95... no
checking for gfortran... no
checking whether we are using the GNU Fortran 77 compiler... no
checking whether  accepts -g... no
checking the maximum length of command line arguments... 32768
checking command to parse /usr/bin/nm -B output from gcc object... ok
checking for objdir... .libs
checking for ar... ar
checking for ranlib... ranlib
checking for strip... strip
checking if gcc supports -fno-rtti -fno-exceptions... no
checking for gcc option to produce PIC... -fPIC
checking if gcc PIC flag -fPIC works... yes
checking if gcc static flag -static works... yes
checking if gcc supports -c -o file.o... yes
checking whether the gcc linker (/usr/bin/ld) supports shared libraries... yes
checking whether -lc should be explicitly linked in... no
checking dynamic linker characteristics... GNU/Linux ld.so
checking how to hardcode library paths into programs... immediate
checking whether stripping libraries is possible... yes
checking if libtool supports shared libraries... yes
checking whether to build shared libraries... yes
checking whether to build static libraries... yes
configure: creating libtool
appending configuration tag "CXX" to libtool
checking for ld used by g++... /usr/bin/ld
checking if the linker (/usr/bin/ld) is GNU ld... yes
checking whether the g++ linker (/usr/bin/ld) supports shared libraries... yes
checking for g++ option to produce PIC... -fPIC
checking if g++ PIC flag -fPIC works... yes
checking if g++ static flag -static works... yes
checking if g++ supports -c -o file.o... yes
checking whether the g++ linker (/usr/bin/ld) supports shared libraries... yes
checking dynamic linker characteristics... GNU/Linux ld.so
checking how to hardcode library paths into programs... immediate
appending configuration tag "F77" to libtool
checking for main in -lfuse... yes
checking for main in -lncurses... no
checking for main in -lpthread... yes
checking for __gmpz_init in -lgmp... yes
checking for gcry_cipher_open in -lgcrypt... yes
checking for libgcrypt-config... /usr/bin/libgcrypt-config
checking for LIBGCRYPT - version >= 1.2.0... yes
checking LIBGCRYPT API version... okay
checking for ANSI C header files... (cached) yes
checking arpa/inet.h usability... yes
checking arpa/inet.h presence... yes
checking for arpa/inet.h... yes
checking fcntl.h usability... yes
checking fcntl.h presence... yes
checking for fcntl.h... yes
checking limits.h usability... yes
checking limits.h presence... yes
checking for limits.h... yes
checking netdb.h usability... yes
checking netdb.h presence... yes
checking for netdb.h... yes
checking stddef.h usability... yes
checking stddef.h presence... yes
checking for stddef.h... yes
checking for stdlib.h... (cached) yes
checking for string.h... (cached) yes
checking for strings.h... (cached) yes
checking sys/socket.h usability... yes
checking sys/socket.h presence... yes
checking for sys/socket.h... yes
checking sys/time.h usability... yes
checking sys/time.h presence... yes
checking for sys/time.h... yes
checking syslog.h usability... yes
checking syslog.h presence... yes
checking for syslog.h... yes
checking for unistd.h... (cached) yes
checking utime.h usability... yes
checking utime.h presence... yes
checking for utime.h... yes
checking for an ANSI C-conforming const... yes
checking for uid_t in sys/types.h... yes
checking for mode_t... yes
checking for off_t... yes
checking for size_t... yes
checking whether time.h and sys/time.h may both be included... yes
checking for pid_t... yes
checking for unistd.h... (cached) yes
checking vfork.h usability... no
checking vfork.h presence... no
checking for vfork.h... no
checking for fork... yes
checking for vfork... yes
checking for working fork... yes
checking for working vfork... (cached) yes
checking for stdlib.h... (cached) yes
checking for GNU libc compatible malloc... yes
checking sys/select.h usability... yes
checking sys/select.h presence... yes
checking for sys/select.h... yes
checking for sys/socket.h... (cached) yes
checking types of arguments for select... int,fd_set *,struct timeval *
checking for bzero... yes
checking for gethostbyname... yes
checking for gettimeofday... yes
checking for inet_ntoa... yes
checking for memset... yes
checking for select... yes
checking for socket... yes
checking for strchr... yes
checking for strerror... yes
checking for strstr... yes
checking for strtol... yes
configure: creating ./config.status
config.status: creating Makefile
config.status: creating config.h
config.status: config.h is unchanged
config.status: executing depfiles commands
jagman@Dexlap:~/afpfs-ng-0.4.1$ make
make  all-am
make[1]: Entering directory `/home/jagman/afpfs-ng-0.4.1'
if gcc -DHAVE_CONFIG_H -I. -I. -I.    -g -Wall -D_FILE_OFFSET_BITS=64  -g -O2 -MT afpfsd-commands.o -MD -MP -MF ".deps/afpfsd-commands.Tpo" -c -o afpfsd-commands.o `test -f 'commands.c' || echo './'`commands.c; \
        then mv -f ".deps/afpfsd-commands.Tpo" ".deps/afpfsd-commands.Po"; else rm -f ".deps/afpfsd-commands.Tpo"; exit 1; fi
commands.c:9:27: error: fuse/fuse_opt.h: No such file or directory
In file included from commands.c:25:
afp.h:11:1: warning: "FUSE_USE_VERSION" redefined
In file included from /usr/include/fuse/fuse.h:19,
                 from /usr/include/fuse.h:9,
                 from commands.c:8:
/usr/include/fuse/fuse_common.h:17:1: warning: this is the location of the previous definition
commands.c: In function ‘start_fuse_thread’:
commands.c:145: warning: implicit declaration of function ‘get_debug_mode’
commands.c:160: warning: passing argument 2 of ‘afp_register_fuse’ from incompatible pointer type
commands.c: In function ‘process_mount’:
commands.c:635: warning: passing argument 3 of ‘new_server’ from incompatible pointer type
make[1]: *** [afpfsd-commands.o] Error 1
make[1]: Leaving directory `/home/jagman/afpfs-ng-0.4.1'
make: *** [all] Error 2
jagman@Dexlap:~/afpfs-ng-0.4.1$ sudo make install
if gcc -DHAVE_CONFIG_H -I. -I. -I.    -g -Wall -D_FILE_OFFSET_BITS=64  -g -O2 -MT afpfsd-commands.o -MD -MP -MF ".deps/afpfsd-commands.Tpo" -c -o afpfsd-commands.o `test -f 'commands.c' || echo './'`commands.c; \
        then mv -f ".deps/afpfsd-commands.Tpo" ".deps/afpfsd-commands.Po"; else rm -f ".deps/afpfsd-commands.Tpo"; exit 1; fi
commands.c:9:27: error: fuse/fuse_opt.h: No such file or directory
In file included from commands.c:25:
afp.h:11:1: warning: "FUSE_USE_VERSION" redefined
In file included from /usr/include/fuse/fuse.h:19,
                 from /usr/include/fuse.h:9,
                 from commands.c:8:
/usr/include/fuse/fuse_common.h:17:1: warning: this is the location of the previous definition
commands.c: In function ‘start_fuse_thread’:
commands.c:145: warning: implicit declaration of function ‘get_debug_mode’
commands.c:160: warning: passing argument 2 of ‘afp_register_fuse’ from incompatible pointer type
commands.c: In function ‘process_mount’:
commands.c:635: warning: passing argument 3 of ‘new_server’ from incompatible pointer type
make: *** [afpfsd-commands.o] Error 1
jagman@Dexlap:~/afpfs-ng-0.4.1$
theres a turd in this pile of lines.... i can smell it from across  a football field

---

### Post by alexthepuffin on 2007-04-02
What's the output of 

ls -l /usr/include/fuse/fuse_opt.h

?

And is this feisty?

- A

---

### Post by LdrJagMan on 2007-04-02
checking and no this is dapper drake 6.06.1....
that file is non-existent on this machine...

---

### Post by alexthepuffin on 2007-04-02
Ah.  If I understand correctly, this is fuse 2.4.2.  I've never run afpfs-ng on anything earlier than 2.5 and the API changes between those two.

This is not hard, but not quite trivial.  You'd have to change:
- get rid of fuse_opt.h includes (they're not needed anyway, I'll get rid of them)
- in afp.h, set FUSE_VERSION to 21 instead of 25
- redo some of the directory functions (readdir needs to be redone with getddir())
- probably some other fuse API changes

If you're new to Linux, an easier approach may be to use a newer version of Ubuntu

Sorry...

- Alex

---

### Post by LdrJagMan on 2007-04-02
well better get my blasting gear and get to it,,,, give me some addresses....
because the only time ime gonna change this thing is when i either get a nice disk of vista or this becomes outdated....
and dont be sorry i have to learn this crap because i am going to be an IT guy in the future...

---

### Post by LdrJagMan on 2007-04-02
sorry for the double post but I have one thing to say... step 2 is compleat.... and dapper is suppose to be the long term support thing... why is everyone abaddoing ship....

---

### Post by alexthepuffin on 2007-04-03
afpfs-ng is really bleeding edge, the developers (mostly me) need to focus on later technologies.  Those distributions all have fuse 2.5 or later.

As afpfs-ng stabilizes, it will be more appropriate for stable distros like Dapper.

That said, if someone generated a patch to support FUSE 2.4, I'd definitely apply it.

- Alex

---

### Post by LdrJagMan on 2007-04-03
hrm a fuse 2.4 patch... time to start buggin people!:lolflag:

---

### Post by LdrJagMan on 2007-04-04
score a point for me:guitar:  and the dapper drake users i found out how to put fuse 2.5.3 on dapper:) 
[http://www.debuntu.org/2006/06/26/71-fuse-253-for-ubuntu-dapper]("http://www.debuntu.org/2006/06/26/71-fuse-253-for-ubuntu-dapper")
Now will that version of fuse work for this project or am i still boned....:confused:

---

### Post by alexthepuffin on 2007-05-04
That should work.

---

### Post by Unclesmiff on 2007-05-12
Does anyone know where I can get rtld from?

rpm -i afpfs-ng-0.4.1-1.i386.rpm
error: Failed dependencies:
        rtld(GNU_HASH) is needed by afpfs-ng-0.4.1-1.i386

---

### Post by alexthepuffin on 2007-05-13
You probably have a glibc mismatch between the system the binary RPM was built on and what you're trying to run it on.  

You may want to grab the source rpm, then rebuild using rpmbuild--rebuild afpfs-ng-0.4.1-1.src.rpm (or similiar).

What distro are you running?

- Alex

---

### Post by fatlotus on 2007-10-05
I've gotten this to work from a deb in fiesty and everything works perfectly, but I can't seem to mount my home directories. Note: In OSX Server, the homedirs are aliased as the user name.


Any ideas?

---

### Post by alexthepuffin on 2007-10-05
I suspect that you have a userid mapping problem.

Am I right in thinking that you are mapping something like /home?

Do both the client and server have the same uid/username mapping through something like NIS?

What does 'afp_client status' give you?

- Alex

---

### Post by fatlotus on 2007-10-06
Sorry,. I was kind of vague. I'm trying to connect to a Mac OS X Server installation, I think.

Here are the possible volumes to connect to:

Public
Projects
<my username>

Of the two, only the first two, the ones that can be seen by everybody, are mountable. The last one can be mounted perfectly fine, but I cannot see any files in the mountpoint.

I have installed libfuse_dev, or whatever.

Here's my connect command:

mkdir /tmp/afp
afp_client mount -u <username> -p - <serverurl>:<username> /tmp/afp

Note: The server is down, so I won't be able to get a trace yet..

---

### Post by alexthepuffin on 2007-10-06
Okay, I see the problem too now.  You won't see anything in the network capture that's relevant.  This might take me a couple of days, the solution isn't obvious.

- Alex

---

### Post by alexthepuffin on 2007-10-07
This should be fixed in afpfs-ng-0.4.3a now.

Sorry, there's no .deb for it yet.

- Alex

---

### Post by fatlotus on 2007-10-08
Sorry, but what was the problem? Could it instead be a network issue?

Thanks!

---

### Post by alexthepuffin on 2007-10-08
The problem that's fixed in afpfs-ng 0.4.3a is the following.  

The client properly connects and authenticates.  When a volume is connected (using FpOpenVol), it reports back some attributes, and (oddly) without the UnixPriv bit.

After the mount, fuse checks the perms of the root of the mount and because the UnixPriv bit wasn't set, it just doesn't report unix permissions.  So fuse thinks no operations can happen on the mount, and it just reports -EIO for all operations.

Note that I've only seen this behaviour on netatalk servers.

It wouldn't be a network connection problem or you wouldn't see a successful mount for the other volumes.

Could you try out afpfs-ng 0.4.3a?  If that fails, follow the REPORTING_BUGS.txt instructions found in the source tarball.

- Alex

- Alex

---

### Post by fatlotus on 2007-10-08
It turns out there really ISN'T anything in the volume.

I'm now going to hide under a rock.




Wether it was me being stupid or a software glitch, it probably wasn't your library.

---

### Post by alexthepuffin on 2007-10-08
Glad it works.  Let me know if there's any other problems.

- A

---

### Post by empthollow on 2008-01-02
i'm trying to access my computer with the afpfs-ng_0.4.3a-1_i386.deb
program from sourceforge, here is the commmand i am using
```
 afp_client mount -u empthollow -p ****  192.168.2.2:HD gmac 
```
if i put a sudo in front of it, the command works but i can't browse as user because i do not have permissions.  i have added myself to the fuse group and no longer get permission denied fuse errors. Now it just fails to mount
```
mounting HD on gmac
Starting mount.
Creating new connection to server
Actually mounting.
Mounting failed.

```
this error is returned when running the command as a user not as root.
anyone have any ideas??

---

### Post by alexthepuffin on 2008-01-02
I wrote afpfs-ng so maybe I can help.

Some suggestions:
- use a full path to your mountpoint
- ensure that you have ownership and correct permissions of the mountpoint

If that doesn't get you anywhere, follow the attached documentation which will give me a more complete bug report.


- Alex

---

### Post by empthollow on 2008-01-02
i used full mount point but it wasn't until i did the killall afpfsd that i was able to use the command with success.  that daemon must have held some bad info.  anyway, all is working well and thanks for the quick response. 

tell me something else though, i see that you are planning to add gnome-vfs plugins, is there any way to browse available afp servers on the network other than using netcat?

---

### Post by alexthepuffin on 2008-01-02
I'm glad it works.

If you're trying to just see what servers are available, you can use avahi-browse, eg.:

avahi-browse _afpovertcp._tcp

As for the gnome-vfs2 interface... the gnome-vfs2 replacement, gio, is still in flux, so I want to wait until that settles down first.  There's a command line version (like an FTP client) coming in 0.5. 

- Alex

---

### Post by empthollow on 2008-01-02
sounds great, thanks for the tips

---

### Post by empthollow on 2008-01-26
Can't wait until this gets integrated with gnome or even for the command line util in 0.5 but until then i wrote a little front end script using zenity.  It pops up a list of the local afp servers and their ip addresses and leaves it on the screen until you close it.  Subsequently it will ask for username, password, ip, volume, and mount point specifications.  It will then run the command in a pop up box so that you can see the output should there be any errors.  It will then give you the option to remount if there are errors or cancel to continue and open the mounting directory for you. Hope this is useful to someone other than just me.  Here is the script.  Copy and paste it into a text file and give it  execute permissions either through right click -> properties or by ```
chmod +x afpgui
```

I call mine afpgui:
```
#!/bin/bash



remount()
{
if [ "$?" != 0 ] ; then
killall avahi-browse
exit
else
usr=$(zenity --title 'AFP Mount' --entry --width 220 --text "Please enter username:")
fi

if [ "$?" != 0 ] ; then
killall avahi-browse
exit
else
pwd=$(zenity --title 'AFP Mount' --entry --width 220 --text "Please enter password:")
fi

if [ "$?" != 0 ] ; then
killall avahi-browse
exit
else
svr=$(zenity --title 'AFP Mount' --entry --width 220 --text "Please enter server ip:")
fi

if [ "$?" != 0 ] ; then
killall avahi-browse
exit
else
vol=$(zenity --title 'AFP Mount' --entry --width 220 --text "Please enter volume:")
fi

if [ "$?" != 0 ] ; then
killall avahi-browse
exit
else
mnt=$(zenity --file-selection --directory --title 'Select Mount Point' --width 220 --text "Please enter mount point:")
fi

afp_client mount -u $usr -p $pwd $svr:$vol $mnt | zenity --text-info --height 300 --width 700
zenity --question --text 'do you want to try mounting again?'
	if [ "$?" = "0" ] ; then
		remount
	else
gnome-open $mnt
killall avahi-browse
fi
exit
}

domount()
{
avahi-browse -rk  _afpovertcp._tcp | zenity --title "Local Servers" --text-info --height 700 --width 700 &
sleep 1
remount
}

unmount()
{
afp_client exit | zenity --title 'AFP Exit' --text-info --width 500 --height 300
exit
}


selection=$(zenity --height=200 --width=400 --list  --title 'AFP Mount' --text '' --radiolist  --column "Choose" --column "Action" FALSE "Mount" FALSE "Unmount"); echo $selection
	case "$selection" in
		"Mount"				) domount ;; 
		"Unmount"			) unmount ;;
		
	esac

```

---

### Post by empthollow on 2008-02-10
I am having an error that i think may be a bug.  At random it seems sometimes before i unmount and sometimes after the folder that i used as the mount point in nautilus will look like a file.  In the terminal i can cd into it but when i do an ls it gives me this.
```
ls: .: Transport endpoint is not connected
```
any ideas?

---

### Post by alexthepuffin on 2008-05-01
This is a bug, afpfsd has crashed.

Could you do this:
- run 'afpfsd -d' in a terminal
- do your mount, get to the point of failure
- post the output here


- Alex

---

### Post by garrydolley on 2008-05-01
Hi Alex,

Has anyone contacted you and made a Ubuntu package?  If not, I can make one (already did on my own machine).

---

### Post by alexthepuffin on 2008-05-02
There's an ubuntu package on the afpfs-ng download page. 

- Alex

---

### Post by decoherence on 2008-06-25
For anyone reading this 15 month old thread, there is now an installable .deb for afpfs-ng package on the project's sourceforge site.

[http://sourceforge.net/project/showfiles.php?group_id=179882&package_id=208206&release_id=582751](http://sourceforge.net/project/showfiles.php?group_id=179882&package_id=208206&release_id=582751)

thanks for your work, alex!

---

