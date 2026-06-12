---
title: "kernel update=Things going badly wrong."
date: 2009-03-08
forum: General Help
---

### Post by ceaser_salad on 2009-03-08
Hello

Specs: Acer aspire one, hardy heron

The story so far:
This started with my wireless router. I just could find a signal from my router, after days of restarting, restoring factory its settings etc. So in desperation(like using a hammer when you cant fix something), I started fiddling with my network settings, and for some reason I deleted some of the entries in the 'hosts' section. Needless to say, nothing happened.

What did happen though, was that every time I tried to open synaptic, I would see the usual signs of a program starting(tabs appearing...), and then nothing. Also my web browser would do the same, but after a while it would actually appear. Then i noticed that if I removed my network cable, everything worked as it should.

So, not knowing what I was doing, I decided to do a kernel update to try and restore things. Couldnt use synaptic, so I tried terminal. Must have been using the wrong codes, since I couldnt find anything there.
Then I found KernelCheck. And that said it could install 2.6.28-7(I was running 2.6.24-22 at the time), so I couldnt resist. 

After that update, everything seemed the same, except that my sound card wasnt working, plus my video was stuffed(couldnt use movie player). 
So I thought I'd try redoing the kernelcheck thing, and seeing if I could find solutions during the options part of the install. Dindt see anything, so I aborted :-)


Now I'm left with a 2.6.28.7-ultimate needs to be reinstalled message whenever I try synaptic or apt-get. 

Really, I'd just like to revert back to a stable kernel, and restore my network settings if thats possible.

Any help is appreciated!

Thanks
Emile

---

### Post by zvacet on 2009-03-08
```
cat /etc/hosts
```
 
post it here then somebody can see how it looks now and try to help you to add lines you deleted.

---

### Post by ceaser_salad on 2009-03-08
Ok, heres what I get:

```
emile@ubuntu:~$ cat /etc/hosts
127.0.0.1 localhost

# The following lines are desirable for IPv6 capable hosts
::1 ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts
emile@ubuntu:~$ 

```

---

### Post by zvacet on 2009-03-08
Boot in your old kernel and type in terminal

```
gksudo gedit /etc/hosts
```

Make sure that first two lines looks

127.0.0.1 localhost
127.0.1.1 hostname

Save and close file.Restart and you should be fine.

EDIT:** hostname= your comp name**

---

### Post by ceaser_salad on 2009-03-08
Thank you ZVACET! Saved my bacon :-) 

Who would have thought one single line would have such an impact! With the line back in, I was able to remove the new kernel,and during that process 2.6.24-23 was reinstalled. 
I had issues with that kernel in the past as it caused kernel panics on start up. 
I therefore reverted back to ...-22.

Can the kernel panic issue be fixed, or do i have to uninstall '23 again?

Thanks

---

### Post by zvacet on 2009-03-08
Do you get any error messages?If yes write it here and I believe somebody will help you to solve that problem.You can also look [here]("http://ubuntuforums.org/tags.php?tag=kernel+panic") for finding possible solutions.

---

### Post by ceaser_salad on 2009-03-09
Looking at those threads, "kernel panic 8.04.2", sums up exactly whats wrong. 
Theres also a link in that post, to a bug report. And although there are a few tricks mentioned that sort of work, I think I'll just rollback to my '22 kernel, and be happy.

Thank you for your trouble :-)

---

