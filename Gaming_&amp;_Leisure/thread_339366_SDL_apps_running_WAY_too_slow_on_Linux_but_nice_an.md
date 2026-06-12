---
title: "SDL apps running WAY too slow on Linux but nice and fast on Windows... SDL's fault?"
date: 2007-01-15
forum: Gaming &amp; Leisure
---

### Post by jryfle on 2007-01-15
Hi there, post #1 woo hoo

So I'm playing an SDL game on a friend's Windows computer. Super Mario War. Oh, this is fun, I say. Knowing it's an SDL game, I check its website for a Linux version. Sure enough, there's Linux binaries and source. Don't feel like waiting a few hours to compile one bleeding game so I grab the binary. Great.

So I install it, very nice. Run the game. Here we go, the hiccup. THE GAME IS TOO SLOW! Seriously, the nice smooth graphics I saw on my mate's Windows PC has turned to an awful frame skip which makes my eyes hurt. The game isn't slow. It just skips every billion frames or so.

I deduced it isn't a game issue, specific to that game. Or to the port either. All of my SDL programs have an arduous frame skip. But this game is important to me, it's actually kind of decent. I really want to play it on my Xubuntu box.

For background information, I've got an nvidia video card with the latest binary drivers from the website. Don't bother saying "maybe your card doesn't support it well", cos my friend has the same card. We've got more or less the same of everything in our computer, we buy from the same place lol.

Thankya if you can tell me if its SDL's fault, or xlib's (Windows SDL uses DirectX, Linux one uses xlib... maybe that's a huge difference which must be accounted for??), or whatever it is. 

:)

---

### Post by jryfle on 2007-01-18
bump

---

### Post by DoktorSeven on 2007-01-18
I believe because SDL uses DirectDraw on Windows which takes advantage of any hardware acceleration.  On Linux, SDL alone won't use acceleration -- you can use an OpenGL surface to draw on to do hardware acceleration, but by default normal SDL surfaces are done without acceleration.

Therefore drawing onscreen in Linux using SDL is slower.

---

### Post by jryfle on 2007-01-19
Thank you :)

I only asked because I asked the SDL channel on FreeNode but they didn't believe me when I said it was slower. I've read up about SDL rendering with OpenGL, but it looks like it has to be coded into the software. No chance of ... forcing SDL to render OpenGL? lol.

---

### Post by DerajSF on 2012-02-18
SDL_SemWaitTimeout is another possibility. Do not use that function because it is very inefficient in some implementations (effectively just polling every 1 ms in a loop).

---

### Post by overdrank on 2012-02-18
[IMG]http://img147.imageshack.us/img147/5451/necromancing.jpg[/IMG]

---

