---
title: "Need some help performing this task"
date: 2006-02-22
forum: Desktop Environments
---

### Post by Mykas0 on 2006-02-22
Hi.

Basically I have two computers, a desktop and a portable one. What I want to do is connect to my desktop one (by SSH) and download some files to my current one.
Doing this is generally easy ("wget" all the way...) but sometimes I want larger files which wouldn't fit in my old computer with its 2 Gb disk. So, I wanted to download the file in the other computer BUT redirect the transfer immedeatly to my current one. Any ideas on how to do it?

I hope I explained my problem in a easy way...

---

### Post by Sendervictorius on 2006-02-23
Can you please give us more details, so we understand your set up. Are the two computers connected via a lan to each other? Are they both connected to the internet? are they both running Ubuntu? Is one running a web server, and the other wgets files from the server???

---

### Post by engla on 2006-02-23
you can in some way use ssh port forwarding to help you. I'm not an expert on this, though..

---

### Post by Mykas0 on 2006-02-23
Ok, I will try to be more specific. There are two computers:

COMPUTER A
- Desktop, currently at home
- Has Ubuntu
- Has a 2 Gb disk, with like.... only 500 Mb free
- Always at home, with internet connection

COMPUTER B
- Portable
- Has Ubuntu
- Has a large disk
- Always with me

Basically, what I would generally do is:

> 
Connect to computer A by SSH
wget file_here
copy the file from computer A to computer B


However, this has a slight problem. In case I want to download a big file (larger than 500 Mb) I wouldn't be able to host it temporarily in computer A. So, what I wanted to do was downloading it on computer A AND, while downloading it from that computer, the download "chunks" would be instantly transfered to computer B.

And why is this? Well, computer A has a great connection, while computer B usually has a lot slower one.

Any ideas?

---

### Post by lamego on 2006-02-23
It seem you want to share the internet connection from computer A .
This [thread]("http://www.ubuntuforums.org/showthread.php?t=91370") may help you.

---

### Post by Sendervictorius on 2006-02-25
I agree, it does sound like you are wanting to set up computer A as a NAT router, and allow computer B to access the internet.

lamego's suggested thread may be useful, but I would be inclined to do it with GUI tools. Firestarter's wizard does it all with the click of a few buttons.

Install firestarter from synaptic on computer A, if you haven't already got it. Then  follow the setup wizard. Be sure you check the box which says "Enable Internet connection sharing", and you should be away laughing! :-D

I'm not entirely sure what the SSH bit in your explanationis all about, which makes me think I may be missing something. If computer A and computer B are next to each other, and connected on a local ethernet, why do you need SSH?

Edit later: Ahh, I think I see. You login to computer A from computer B using SSH, then execute wget on computer A to download the files you are after. Then you copy the files to computer B.

If you configure computer A to share the internet, you can now execute your wget commands from computer B.

---

### Post by Mykas0 on 2006-03-14
And can share a connection when they are more than 200 Km away from each other? o_O

---

