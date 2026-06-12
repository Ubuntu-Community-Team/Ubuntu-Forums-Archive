---
title: "Pointers on file sharing vista ubuntu"
date: 2009-01-14
forum: General Help
---

### Post by nothingspecial on 2009-01-14
I`m a noooob (always wanted to say that)

Tomorrow, I`m installing ubuntu on my brothers old pc. It`s virused up and slow. He want`s to use it as a media server. He has a brand new shiny vista laptop. He want`s to be able to access files on the ubuntu box from the vista laptop.

I have never used windows, I haven`t the first idea. (nooooob)

There`s alot of info online about how to do this but I`m struggling with the windows side of things.

Can anyone (if they`ve got a minute) point me to a complete idiots guide to doing this? 

I don`t need help on the linux side. If he`d let me install ubuntu on his new laptop, it`d be up and running in 15 mins, so I`ll stress again, it`s the windows side I`m going to struggle with.

Thanks

---

### Post by adamitj on 2009-01-14
Hehe, and I always searched for someone as so pure as you :)

Well, let's start from the communication protocol. As I see, you want to access files in a Ubuntu OS from a Vista OS. So, let me assume you're trying to do this from shared folders, within windows is possible by SMB protocol:

1) Install samba and samba-client in your Ubuntu based desktop;
2) Configure your shared folders by editing the /etc/samba/smb.conf file (needs samba process to be restarted);
3) Access the shared folders in your network by typing "\\<machine_name_or_ip>\<name_of_share>" from your Vista OS.

Notice that sometimes the local names aren't recognized as they are accessible by simple typing the ip address. Ex.:

\\10.0.0.120\music

This is only a simple description of what you need to do. Let me know if you need further assistance, or if I couldn't get your real needs...

Cheers!

---

