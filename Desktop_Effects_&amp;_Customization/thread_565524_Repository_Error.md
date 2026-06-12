---
title: "Repository Error"
date: 2007-10-02
forum: Desktop Effects &amp; Customization
---

### Post by hydroweaver on 2007-10-02
hey guyz im using fiesty and i was trying customization to vista from the ultimate guide...

however  whenever i hapn to use : _deb [http://hendrik.kaju.pri.ee/ubuntu](http://hendrik.kaju.pri.ee/ubuntu) feisty screenlets_ in the third party softwares
and reload it... the following error appears : 

**W: GPG error: [http://hendrik.kaju.pri.ee](http://hendrik.kaju.pri.ee) feisty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 3C33E735F854AFD7**

can u guyz help me out wid the screenlets 

thnk u in advance

---

### Post by FuturePilot on 2007-10-02
It nothing to be worried about really. It's just saying that you don't have a gpg key for that repo to authenticate it.
If you want to get rid of the warning try this
```
wget http://hendrik.kaju.pri.ee/ubuntu/hendrikkaju.gpg -O- | sudo apt-key add -
```
```
sudo apt-get update
```
It should be gone then:)

---

### Post by hydroweaver on 2007-10-02
thnk u for ur help.... but the same problem persists !!.....

---

### Post by hydroweaver on 2007-10-02
i guess i was using the ternimal in a wrong way....thnk u so much....!!

---

### Post by hydroweaver on 2007-10-02
how do i learn ubuntu or linux like u ...or other pro's who r here ?
it wud b a greatful of u to provide me some advices....thnk u again !

---

### Post by Rupertronco on 2007-10-02
I've only used linux for 6 months, and I started with slackware. It was probably the worst idea in the world from a simplicity standpoint, if I had properly educated myself I'd have used something else. In hindsight I'm happy I selected slackware because it forced me to use the command line exclusively to do anything initiallyt. It was a very difficult process, but it taught me a great deal about linux. 

The best way to learn linux is to use it. And read, read, read. read. Try new things. Get familiar with the command line. Most people are scared of it, but in reality it's the most powerful tool you have in linux. Many people follow howtos for many things, but when you're following a howto thread, try to understand what commands are being put in the terminal, and what they do, instead of just copying and pasting.

---

### Post by FuturePilot on 2007-10-02
> **hydroweaver said:**
> how do i learn ubuntu or linux like u ...or other pro's who r here ?
it wud b a greatful of u to provide me some advices....thnk u again !

One piece of good advice is to stick with it from the OMG! that's the coolest feature to the Grrrr, I want to rip out my hair why won't this work times. I've been using Ubuntu for a little over a year and there's still a lot of stuff I don't know. I'm still learning new things all the time. I've broken the system numbers of times:lolflag: I've learned a lot of things through trial and error and just hanging around these forums. 

I've found this to be a good resource as well
[http://www.ubuntuguide.org]("http://www.ubuntuguide.org")
There's also a lot of good stuff on this site too
[http://www.psychocats.net/ubuntu/index]("http://www.psychocats.net/ubuntu/index")

---

### Post by peterson2k4 on 2007-11-29
you are a life saver thanks a million

---

