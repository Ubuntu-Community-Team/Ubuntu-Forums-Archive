---
title: "Are these LAN games?"
date: 2009-02-08
forum: Gaming &amp; Leisure
---

### Post by Rytron on 2009-02-08
Hi.
These are great games. Can someone confirm if they are or are not LAN games? Or is it only possible to play multiplayer over the internet.
nexuiz
tremulous
urban terror
warsow

PS I can confirm that these **are** LAN games:
Armagetron Advanced
Enemy Territory
Open Arena

---

### Post by crazyfuturamanoob on 2009-02-08
All Q3 based games can be played over LAN.

---

### Post by kutagh on 2009-02-08
Correct, those 4 are Quake 3 engine based. When setting up a server, you pick LAN instead of Internet.

---

### Post by Rytron on 2009-02-08
Thanks guys, I'll check that out now.

---

### Post by Rytron on 2009-02-08
With Urban Terror there is an option for dedicated: no, LAN , Internet. If I choose either LAN or Internet the game closes itself. What settings must I have to create a server for a LAN game?

For tremulous there is an option for LAN but when I choose that, the games closes itself just like urban terror.

For nexuiz I don't see an option to set up a LAN server!

In warsow I don't see an option to set up a LAN server either!

Could someone tell me the correct settings for some/all of the above games?

---

### Post by kutagh on 2009-02-08
I think that you should rather try to utilize the sites of those games as they got a bunch of help ready for you if you just search :)

---

### Post by PrimoTurbo on 2009-02-08
Like it was mentioned before all of these games should be able to run on LAN.

You can try finding out your internal LAN ip normally something like this: 192.168.0.X (Use ifconfig in terminal or ipconfig on windows CMD) then you launch the game bring down the console and load a map that you know. Just type in "map mapname" then try to connect from another computer to your internal network ip through "connect 192.168.0.X" or whatever your ip address is, sometimes you might need to provide the port and maybe even forward it through your router if you are using one.

---

### Post by Rytron on 2009-02-09
> **PrimoTurbo said:**
> Like it was mentioned before all of these games should be able to run on LAN.

You can try finding out your internal LAN ip normally something like this: 192.168.0.X (Use ifconfig in terminal or ipconfig on windows CMD) then you launch the game bring down the console and load a map that you know. Just type in "map mapname" then try to connect from another computer to your internal network ip through "connect 192.168.0.X" or whatever your ip address is, sometimes you might need to provide the port and maybe even forward it through your router if you are using one.

Hi. I am not using a router. I just connect the laptop and desktop computers via crossover cable. There was zero hassle when setting up Armagetron Advanced, Enemy Territory and Open Arena for LAN games.

---

### Post by Frem on 2009-02-10
You still have an IP address. Type "ifconfig" in the terminal; it'll be in the info that comes up.

---

### Post by Rytron on 2009-02-11
Hi.
If anyone has these games working over a LAN, please could you post how you did it. Thanks.

nexuiz
tremelous
warsow

:confused:

---

### Post by Rytron on 2009-09-05
All the games I have gotten to work via a LAN:
Armagetron Advanced
AssaultCube 1.0.2
Enemy Territory
Open Arena

---

### Post by noerrorsfound on 2009-09-05
> **Rytron said:**
> AssaultCube 1.0.2
Upgrade to 1.0.4.

---

### Post by RabidWeezle on 2009-09-06
for quake engine based games:

run ifconfig in a terminal on the "host" machine:

it will give you the IP to that machine, write it down. When I refer to this ip address, I will call it <host>

Create a match in that game.

Start up the other machine, test to make sure that machine is talking to the other one properly over the crossover cable:

```
ping <host>
```

if it pings you are good. If it doesn't then you aren't using the right ip, or a network setting is borked.

Start the game on the client, go into the console and type in:

```
/connect <host>
```

that should connect up UNLESS the host and client have different versions of the game, or a firewall on the host system not setup to open the port needed to run the game.

If you can't open the game console (most time it's opened from pressing tilda (the button before 1/! on the upper left of the keyboard, then this is how you do it.

Start the game on the host, wait for it to load, when it's done start the game on the client with the command line: "<name of executable> +connect <host>:<port>", example:

```
quake3 +connect 192.168.0.0:27960
```

If you don't specify a non-standard port on the host, you don't have to put the port in there or the : like so

```
nexuiz-glx +connect 192.168.0.0
```

Hope that helps.

---

### Post by Rytron on 2009-09-06
Thank you RabidWeezle. I will put your advice to the test.

---

