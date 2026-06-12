---
title: "Could Not  Download All Respository Idexes"
date: 2009-04-13
forum: Dell Ubuntu Support (CLOSED)
---

### Post by Kensoi on 2009-04-13
Hi. I Received This Message (Please See Attachment)

I'm Still New To Ubuntu So I Would Appreciate Some Help.
I Also Included Source List (Please See 2nd Attachment)

Thanks 
        Ken

---

### Post by antikristian on 2009-04-13
There are three repositories in your sources.list that point to a directory on archive.ubuntu.com that is no longer there

Change "archive.ubuntu.com" and "security.ubuntu.com" to "ports.ubuntu.com" and refresh synaptic:)

Leave the rest as they are:)

---

### Post by Kensoi on 2009-04-14
Hi & Thanks For That. I Will Try The Changes & See How I Get On.
Cheers.

---

### Post by Kensoi on 2009-04-14
I  Have Tried Changing The Settings On The Sources List.       New entries should look like this: 

	  deb [http://ports.ubuntu.com/ubuntu-ports](http://ports.ubuntu.com/ubuntu-ports) hardy main restricted
	deb [http://ports.ubuntu.com/ubuntu-ports](http://ports.ubuntu.com/ubuntu-ports) hardy-security main restricted
	

It Will Not Allow Me. Can Anyone Tell Me The Easiest Way To Do This ?

I Am Being Told I'm Not The Owner & Can't Change The Permissions.

As I Said Before I Am New To Ubuntu & Find It Difficult The Way Some Of The Instructions Are Written & Would Welcome Someone To Point Me On How I Can Change These Permissions. 

I'm Finding Editing Sudoers File A Bit Confusing.


Thanks Ken.

---

### Post by antikristian on 2009-04-14
run ```
gksudo gedit /etc/apt/sources.list
``` to run gedit as root

according to your existing sources list, only change

deb [http://archive.ubuntu.com/ubuntu-ports](http://archive.ubuntu.com/ubuntu-ports) hardy main
deb [http://security.ubuntu.com/ubuntu-ports](http://security.ubuntu.com/ubuntu-ports) hardy-security main
deb [http://archive.ubuntu.com/ubuntu-ports](http://archive.ubuntu.com/ubuntu-ports) hardy-updates main

to 

deb [http://ports.ubuntu.com/ubuntu-ports](http://ports.ubuntu.com/ubuntu-ports) hardy main
deb [http://ports.ubuntu.com/ubuntu-ports](http://ports.ubuntu.com/ubuntu-ports) hardy-security main
deb [http://ports.ubuntu.com/ubuntu-ports](http://ports.ubuntu.com/ubuntu-ports) hardy-updates main

leave all the rest as they are

---

### Post by superm1 on 2009-04-14
When using the mini9 with the factory shipped image, all your repositories should be from dell-mini.archive.canonical.com.  You shouldn't be having any from archive.ubuntu.com or ports.ubuntu.com.
If you do, you should remove them.

---

### Post by Kensoi on 2009-04-14
Thanks For The Above Posts. Will Have A Go Tomorrow.

Thanks Again. Ken

---

### Post by Kensoi on 2009-04-15
Taking Them Off Altogether Done The Trick. 

Thanks.

---

### Post by snowpine on 2009-04-15
> **superm1 said:**
> When using the mini9 with the factory shipped image, all your repositories should be from dell-mini.archive.canonical.com.  You shouldn't be having any from archive.ubuntu.com or ports.ubuntu.com.
If you do, you should remove them.

Can you shed any light on why Dell ships the Mini 9 with a broken sources list?

---

### Post by superm1 on 2009-04-15
> **snowpine said:**
> Can you shed any light on why Dell ships the Mini 9 with a broken sources list?
They don't ship with a broken list, but using the software sources tool that shipped you can generate a broken list.  I believe that's where the oversight was.  I seem to think it should have been fixed by web updates (ironically)

---

### Post by duckfeet on 2009-04-17
> **superm1 said:**
> They don't ship with a broken list, but using the software sources tool that shipped you can generate a broken list.  I believe that's where the oversight was.  I seem to think it should have been fixed by web updates (ironically)

Yep: I'm having the exact same problem, and my mini-9 arrived just yesterday...but I tried to update the software sources, and now I'm getting same error message, and it's in some kind of 'loop' too, so I'll try removing those, also....

Much appreciate the info...

---

### Post by JEBB on 2009-04-21
> **superm1 said:**
> They don't ship with a broken list, but using the software sources tool that shipped you can generate a broken list.  I believe that's where the oversight was.  I seem to think it should have been fixed by web updates (ironically)

What is the complete, correct sources list that I should use with my Dell Mini 9 with Ubuntu 8.0.4?  Using your previous instructions, as I understood them, gave me some error messages.  

Thank you

---

### Post by Kensoi on 2009-04-22
At The Very Start Of This Thread A Sources List Is Attached.

On That List There Were Three I Had To Remove. See Attachment.

The Ubuntu.Com Were The Ones I Removed & Leave The Dell Ones.

That's What Worked For Me.

---

### Post by Kensoi on 2009-04-22
[http://ubuntuforums.org/showthread.php?t=1124709](http://ubuntuforums.org/showthread.php?t=1124709)

---

