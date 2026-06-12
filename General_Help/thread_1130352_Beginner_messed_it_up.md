---
title: "Beginner messed it up"
date: 2009-04-19
forum: General Help
---

### Post by Damouf on 2009-04-19
Hello,

I just tryed to play with the terminal using sudo to install playonlinux and now Synaptic, Package installer and Update manager (at least) are not running anymore... Here are the error message I get :

For Synaptic:

E: Type &#8216;--2009-04-19&#8217; is not known on line 1 in source list /etc/apt/sources.list.d/playonlinux.list
E: The list of sources could not be read.
Go to the repository dialogue to correct the problem.
E: _cache->open() failed, please report.

For Package manager:

This is a major failure of your software management system. Please check for broken packages with synaptic, check the file permissions and correctness of the file '/etc/apt/sources.list' and reload the software information with: 'sudo apt-get update' and 'sudo apt-get install -f'. 

And Update manager:

'E:Type &#8216;--2009-04-19&#8217; is not known on line 1 in source list /etc/apt/sources.list.d/playonlinux.list, E:The list of sources could not be read.'

I am a complete linux beginner so could you help me please, I have no idea what to do:(

Thanks in advance,

Damien.

---

### Post by lisati on 2009-04-19
The first thing to try is what is suggested by the error message.

From the command line, type the following:
```
sudo apt-get update
sudo apt-get install -f

```

---

### Post by codeseer on 2009-04-19
At the top left of your screen click System->Administration->Software Sources. Enter your password at the prompt and click OK. Click on the second tab of this new window, labeled 'Third-Party Software'.

What is there in the list, besides these:

[http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) intrepid partner
[http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) intrepid partner (Source Code)

---

### Post by Damouf on 2009-04-19
Got this :-(

ln-dam@ln-dam-desktop:~$ sudo apt-get update
[sudo] password for ln-dam: 
E: Type &#8216;--2009-04-19&#8217; is not known on line 1 in source list /etc/apt/sources.list.d/playonlinux.list
ln-dam@ln-dam-desktop:~$ sudo apt-get install -f
E: Type &#8216;--2009-04-19&#8217; is not known on line 1 in source list /etc/apt/sources.list.d/playonlinux.list
E: The list of sources could not be read.

---

### Post by lisati on 2009-04-19
> **Damouf said:**
> Got this :-(

ln-dam@ln-dam-desktop:~$ sudo apt-get update
[sudo] password for ln-dam: 
E: Type ‘--2009-04-19’ is not known on line 1 in source list /etc/apt/sources.list.d/playonlinux.list
ln-dam@ln-dam-desktop:~$ sudo apt-get install -f
E: Type ‘--2009-04-19’ is not known on line 1 in source list /etc/apt/sources.list.d/playonlinux.list
E: The list of sources could not be read.

Next thing to check: go with codeseer's suggestion.

---

### Post by ddrichardson on 2009-04-19
Can you post  /etc/apt/sources.list.d/playonlinux.list - it's corrupted or in the wrong format. You can also untick it from System->Administration->Software Sources

---

### Post by Damouf on 2009-04-19
Hi codeseeder,

There is nothing but only what you mentionned...

Does it help?

---

### Post by Damouf on 2009-04-19
Hi Richardson,

What means "Can you post /etc/apt/sources.list.d/playonlinux.list"?

Thanks,

Damien.

---

### Post by ddrichardson on 2009-04-19
> **Damouf said:**
> Hi Richardson,

What means "Can you post /etc/apt/sources.list.d/playonlinux.list"?

Thanks,

Damien.
Open a terminal and type:```
cat /etc/apt/sources.list.d/playonlinux.list > ~/weirdsource.lst
```Then, in your home folder there is a file called "weirdsource.lst", post it (attach it to a post) here.

---

### Post by Damouf on 2009-04-19
OK thanks I got it, here it is:

--2009-04-19 18:41:46--  [http://deb.mulx.net/playonlinux_hardy.list](http://deb.mulx.net/playonlinux_hardy.list)
Resolving deb.mulx.net... 91.121.238.209
Connecting to deb.mulx.net|91.121.238.209|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 174 [text/plain]
Saving to: `playonlinux_hardy.list.2'

     0K                                                       100% 35.5M=0s

2009-04-19 18:41:46 (35.5 MB/s) - `playonlinux_hardy.list.2' saved [174/174]

---

### Post by codeseer on 2009-04-19
Are you running hardy?

---

### Post by Damouf on 2009-04-19
> **ddrichardson said:**
> Open a terminal and type:```
cat /etc/apt/sources.list.d/playonlinux.list > ~/weirdsource.lst
```Then, in your home folder there is a file called "weirdsource.lst", post it (attach it to a post) here.

OK thanks I got it, here it is:

--2009-04-19 18:41:46-- [http://deb.mulx.net/playonlinux_hardy.list](http://deb.mulx.net/playonlinux_hardy.list)
Resolving deb.mulx.net... 91.121.238.209
Connecting to deb.mulx.net|91.121.238.209|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 174 [text/plain]
Saving to: `playonlinux_hardy.list.2'

0K 100% 35.5M=0s

2009-04-19 18:41:46 (35.5 MB/s) - `playonlinux_hardy.list.2' saved [174/174]

---

### Post by Damouf on 2009-04-19
> **codeseer said:**
> Are you running hardy?

Humm... no Ubuntu 8.10... intrepid isn't it?

---

### Post by codeseer on 2009-04-19
Run this in the terminal:

```

sudo rm -f /etc/apt/sources.list.d/playonlinux*

```

Then get the .deb package from [here]("http://www.playonlinux.com/script_files/PlayOnLinux/3.4/PlayOnLinux_3.4.deb").

You should then be able to use the package managers normally. Remember to hit the reload button or run the update command from the terminal.

---

### Post by Damouf on 2009-04-19
> **codeseer said:**
> Run this in the terminal:

```

sudo rm -f /etc/apt/sources.list.d/playonlinux*

```

Then get the .deb package from [here]("http://www.playonlinux.com/script_files/PlayOnLinux/3.4/PlayOnLinux_3.4.deb").

You should then be able to use the package managers normally. Remember to hit the reload button or run the update command from the terminal.

Great seems to work now, many thanks!

---

### Post by codeseer on 2009-04-19
Glad to be of assistance. Helping others helps me learn Ubuntu as well.

---

### Post by ddrichardson on 2009-04-19
> **codeseer said:**
> Glad to be of assistance. Helping others helps me learn Ubuntu as well.
Damnit - you play one game of World at War and you miss the chance to follow up!

---

