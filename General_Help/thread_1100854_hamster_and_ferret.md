---
title: "hamster and ferret"
date: 2009-03-19
forum: General Help
---

### Post by t_virus on 2009-03-19
hello all,
is there anyone that can install successfuly hamster and ferret and get it working?
could you please give me a help with this?
there is a tutorial about installing at BT4 but in ubunto is diferent.
[http://hamster.erratasec.com/](http://hamster.erratasec.com/)

---

### Post by TheLions on 2009-03-19
wanabe 1337 Haxx0r?:lolflag:

open terminal
```

wget http://hamster.erratasec.com/downloads/hamster-2.0.0.tar.z
tar -xf hamster-2.0.0.tar.z
cd hamster/build/gcc4
make
cd \..
cd \..cd \..
cd ferret/build/gcc4dynamic
make

```

to run ferret 
type ```
cd \..
cd bin
./ferret
pwd

```
(pwd to display your location of ferret )

to run hamster
type ```
cd \..
cd bin
./hamster
pwd

```
(pwd to display your location of hamster )

---

### Post by t_virus on 2009-03-25
thanks for the replay, but i need some help on other thing:

how do i move ferrret from /bin/ferret to /bin/hamster?

for this to work i need to have the both in the same directory...

thankx for your help.

---

### Post by TheLions on 2009-03-26
just copy it!
:lolflag:

open nautilus (nautilus ~/bin/ferret) and copy it or


in terminal:
```
cp ferret/bin/ferret hamster/bin/
```

---

### Post by t_virus on 2009-03-26
thankx TheLions,
i got it working....

can you answer me one thing?
ferret and hamster only works in promiscous mode, can i get my NVIDIA gFORCE 7000M doing promiscous?

sorry if i trouble you, thankx anyway

::::

mauro@mauro-laptop:~$ ifconfig --help
Utilização:
  ifconfig [-a] [-v] [-s] <interface> [[<AF>] <endereço>]
  [add <endereço>[/<tam-prefixo>]]
  [del <endereço>[/<tam-prefixo>]]
  [[-]broadcast [<endereço>]]  [[-]pointopoint [<endereço>]]
  [netmask <endereço>]  [dstaddr <endereço>]  [tunnel <endereço>]
  [outfill <NN>] [keepalive <NN>]
  [hw <HW> <endereço>] [metric <NN>] [mtu <NN>]
  [[-]trailers] [[-]arp] [[-]allmulti]
  [multicast]  ***_[[-]promisc]_***
  [mem_start <NN>]  [io_addr <NN>]  [irq <NN>]  [media <tipo>]
  [txqueuelen <NN>]
  [[-]dynamic]
  [up|down] ...

---

### Post by TheLions on 2009-03-27
try
```
sudo ifconfig eth0 -promisc
```

---

### Post by t_virus on 2009-03-27
thankx a lot i will try it rioght away

c u next time

mauro

---

### Post by t_virus on 2009-04-03
completely done!!!

thank you

---

### Post by xenophed on 2009-04-03
stealing data from others is just wrong for any reason.I can only hope you will one day see this.

---

### Post by TheLions on 2009-04-03
> **xenophed said:**
> stealing data from others is just wrong for any reason.I can only hope you will one day see this.

having tools != stealing

if I own crowbar that doesn't mean that I'm burglar.
If you own a high-speed Internet connection that doesn't mean that you are pirate...

---

### Post by t_virus on 2009-04-03
my tools are for knowlege, for my own research. 
by the way i test tools in my home network.
i am a network studant and these things can bring me some good know-how.

dont missunderstande me...

---

### Post by loganfynne on 2010-05-04
I have a question. When I am compiling ferret, or hamster, they give me this message. (This is all of what I put in, just in case I made an error)

~$ sudo -s
~# cd ~/ferret/build/gcc4dynamic/
:~/ferret/build/gcc4dynamic# make
gcc -g -I. -I../../src -I../../src/include -Wall -c ../../src/main/main.cpp -o ../../tmp/main.o
gcc: error trying to exec 'cc1plus': execvp: No such file or directory
make: *** [../../tmp/main.o] Error 1

What am I doing wrong?

---

### Post by GreekRockNRoller on 2011-01-15
Hello I am running to the same problem with loganfynne. Could you plz help?

---

### Post by GreekRockNRoller on 2011-01-15
> **loganfynne said:**
> I have a question. When I am compiling ferret, or hamster, they give me this message. (This is all of what I put in, just in case I made an error)

~$ sudo -s
~# cd ~/ferret/build/gcc4dynamic/
:~/ferret/build/gcc4dynamic# make
gcc -g -I. -I../../src -I../../src/include -Wall -c ../../src/main/main.cpp -o ../../tmp/main.o
gcc: error trying to exec 'cc1plus': execvp: No such file or directory
make: *** [../../tmp/main.o] Error 1

What am I doing wrong?
LOL we need g++ to compile. thx jtcgreyfox from [http://www.hak5.org/forums](http://www.hak5.org/forums) for pointing that out!

---

### Post by TheMaverick 666 on 2012-02-11
Hi all, bit of help needed!

I have got ferret and hamster running perfectly within the terminal how ever when i go to [http://hamster](http://hamster) in firefox it just takes me to [www.hamster.com](www.hamster.com). :confused:

I'm sure I'm doing something really stupid but I simply cant figure out what!! 

Any help would be greatly appreciated! :D

TM.

---

### Post by t_virus on 2012-02-11
You have to use proxy like this:

127.0.0.1 on port 1234

save your browser settings using this proxy and type "hamster"

Thats all

---

