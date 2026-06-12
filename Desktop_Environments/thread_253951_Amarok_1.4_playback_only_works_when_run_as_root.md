---
title: "Amarok 1.4 playback only works when run as root"
date: 2006-09-09
forum: Desktop Environments
---

### Post by wouterd on 2006-09-09
Hi all,

I've got this problem that I can't find a solution to anywhere in the forums.

I use Amarok 1.4.3 on Dapper LTS and at first - of course - it wouldn't play mp3's. I got this nice dialogbox from amarok that said: No mp3 support! and asked me whether I wanted it to install the nescessary files. It froze.. 

I tried again, and ran amarok as root from the konsole. MP3 support installed perfectly. MP3 playback works! Hurray! :D 

But when I tried to run amarok as a user again it told me (again) no mp3 support and froze ](*,) 

So I installed all the codecs manually (**libxine-extracodecs**, **w32codecs**, enz) and followed the instructions from 

[INDENT][https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)[/INDENT]

When I restarted amarok as user nothing had happened: dialog box.. freeze.. 
Running as root still works, though.

Can anyone help me out here? Should I change some file permissions in the codecs or anything?


BTW. JuK plays just fine when it outputs to **akode** and **gstreamer**. But not to **arts**..

---

### Post by Junx on 2006-09-09
You could make sure you're in the audio group first.

Then I'd check the permissions of those libraries (you need to be able to read them only; ld-linux.so.2 is the only library that needs to remain executable).

---

### Post by wouterd on 2006-09-09
> **Junx said:**
> You could make sure you're in the audio group first.

Then I'd check the permissions of those libraries (you need to be able to read them only; ld-linux.so.2 is the only library that needs to remain executable).
All libraries in /usr/lib/xine/plugins/1.1.1/ have read permissions for users and I'm also a member of the audio group.

any other ideas?

---

