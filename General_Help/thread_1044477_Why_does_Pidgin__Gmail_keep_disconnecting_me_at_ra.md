---
title: "Why does Pidgin / Gmail keep disconnecting me at random?"
date: 2009-01-19
forum: General Help
---

### Post by ticopelp on 2009-01-19
Every few minutes, when using Gmail chat, I get this message in my buddy list that I've been disconnected. But it won't auto-reconnect, and it doesn't really notify me well -- I have to be watching the buddy list at the time to see the disconnect message, which is extremely annoying. 

Is there any way to get Gmail to auto-reconnect? Does anyone know why this might be happening? I realize it's very little to go on...

Running Intrepid 8.10 with Pidgin 2.5.2. TIA

---

### Post by scouser73 on 2009-01-19
I had sort of the same problem using MSN with my Gmail address under Pidgin, the only thing I could find on Google was this link, hope it helps you. [http://developer.pidgin.im/ticket/5579]("http://developer.pidgin.im/ticket/5579")

---

### Post by Casper Hansen on 2009-07-23
> **scouser73 said:**
> I had sort of the same problem using MSN with my Gmail address under Pidgin, the only thing I could find on Google was this link, hope it helps you. [http://developer.pidgin.im/ticket/5579]("http://developer.pidgin.im/ticket/5579")

The page doesn't work.

---

### Post by geneqew on 2010-01-08
it also disconnects mine at random.. but im using 2 yahoo accounts..

here's are the last few lines i got using **pidgin -d** on terminal before it crashed:

(07:13:53) pidgin-libnotify: Pidgin conversation's widgets are in focus(07:13:53) pidgin-libnotify: Conversation has focus 0xa8d9380
(07:13:54) yahoo: 64 bytes to read, rxlen is 84
(07:13:54) yahoo: Yahoo Service: 0x4b Status: 1
(07:13:54) yahoo: 64 bytes to read, rxlen is 84
(07:13:54) yahoo: Yahoo Service: 0x4b Status: 1
Assertion '!in_worker(m)' failed at pulse/thread-mainloop.c:161, function pa_threaded_mainloop_stop(). Aborting.
Aborted

---

