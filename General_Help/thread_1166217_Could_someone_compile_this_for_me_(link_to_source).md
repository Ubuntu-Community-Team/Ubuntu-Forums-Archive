---
title: "Could someone compile this for me (link to source)"
date: 2009-05-21
forum: General Help
---

### Post by rorkimaru on 2009-05-21
I tried figuring out how to compile software but am in exams and cant work my head around it (too fried!)

What I want to compile is the latest release of Make Human. It's Alpha 2. For A1 they just released a ubuntu download but this time it's source.

If someone would make me an executable (for 9.04) I would be very grateful. I know it's not something for everyone and that people may decide to flame me and call me lazy but in areas where I have expertise I help others. I often help with sample .blends and tips and advice on the Blender Artist's game section (though I've been awol for the last few weeks, exams are ruining my life)

So if you don't mind taking a bit out of your day to help someone else (probably a few people) download and compile the Make Human Alpha 2 source and post a link. I would greatly appreciate it

**[Link to source]("http://code.google.com/p/makehuman/downloads/list")**

---

### Post by wirelessmonkey on 2009-05-21
I'll give you quick instructions to build it yourself...

```

sudo apt-get update
sudo apt-get install python2.5-dev libsdl-image1.2-dev libsdl-net1.2-dev
cd /path/to/makehuman1-0-0_alpha2a_source
sudo chmod +x compile_src.sh
./compile_src.sh
./makehuman

```

---

### Post by rorkimaru on 2009-05-22
Hey it worked!

Thank you very much!! As an aside, can I just upload the folder now and it will work on other Ubuntu PCs?

---

