---
title: "Solution for Beryl white screen bug, without using the slow &quot;--use-copy&quot; option"
date: 2007-06-19
forum: Desktop Effects &amp; Customization
---

### Post by meuge on 2007-06-19
I am loving Ubuntu, and the functionality and beauty of a fully functional Beryl installation are breathtaking. 

But I was cursed with having an ATI X1300 video card in my Inspiron 1505 Dell laptop. As a result, I was relegated to using XGL with the fglrx drivers. 

However, even then, upon launching Beryl my screen would turn white.

The solution I found was to use the following commands:

"$ beryl-xgl --use-copy" to launch beryl
"$ beryl-manager --no-force-window-manager" to launch the beryl manager

This resolved the white cube problem, but it made my system awfully slow and unresponsive. I would get random crashes frequently, and oftentimes videos would skip when maximized or enlarged past a few hundred pixels in size.

Recently I got so frustrated, i was ready to abandon Beryl altogether. But alas, I gave it one more shot, and I discovered a solution that let me use the normal texturing path, as well as to use Beryl as the window manager. 

All you need to do, is to upgrade to the latest Beryl version (the one in SVN repositories) and use the following commands:

"$ beryl-xgl& emerald&" to launch beryl
"$ beryl-manager" to launch the beryl manager

No fancy scripts, no weird workarounds, just a different command to launch beryl. 

And so far, I got the responsiveness back, videos play fine, and I don't get random crashes when using my plasmid DNA modeling software.

---

