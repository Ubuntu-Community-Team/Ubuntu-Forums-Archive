---
title: "Problem opening files over network"
date: 2008-12-27
forum: General Help
---

### Post by lsutiger on 2008-12-27
I installed Ubuntu 8.04 on my media pc yesterday. I have 8.04  on my laptop.
I wanted to share between the two. I decided to use Places-->Connect to server-->SSH to connect. I can browse folders and copy files, but can not open any files.

Is there a better solution to networking the two computers? I marked a folder on the laptop as a "shared folder" but I don't see that certain folder anywhere other than when I use SSH.

Thanx for any input

---

### Post by jerome1232 on 2008-12-27
> **lsutiger said:**
> I installed Ubuntu 8.04 on my media pc yesterday. I have 8.04  on my laptop.
I wanted to share between the two. I decided to use Places-->Connect to server-->SSH to connect. I can browse folders and copy files, but can not open any files.

I'm not sure why you can't open the files... It works fine for me using ssh in this way. Say I'm in gedit, I click file->Open->It has a spot that says ssh://crash@192.168.1.3, I click there and I can open the files up on that server. Everything works as expected

> **lsutiger said:**
> Is there a better solution to networking the two computers? I marked a folder on the laptop as a "shared folder" but I don't see that certain folder anywhere other than when I use SSH.

Thanx for any input
Assuming the laptop your talking about is Hardy or Ibex that means it should be shared as a Windows Share, you can see what Windows Shares are on your network by going Places->Network->Windows Network and having a look around. If that's not working try hitting crtl+l (little letter L not the number 1) and type "smb://ip.address.of.the.laptop/sharename" without the quotes and it should get you there.

---

