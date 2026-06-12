---
title: "Newbie with several Web-related problems"
date: 2006-01-10
forum: Desktop Environments
---

### Post by cesar on 2006-01-10
Hi community,

   I am a junior PHP web application developer. Still becoming re-acquainted with Linux, I have found KUbuntu to be a very impressive product so far. 

   However, there are a few quirks: let me start by enumerating them, 

1) can't play videos in websites from Firefox
2) can't listen to Internet radio in neither Kaffeine nor amaroK
3) would like FireFox as my default browser

and one that's nothing to do with the Internet, but I thought I would squeeze it into here:

4) is there anything like WinXP's 'minimize all' icon?

Now I will go into each of them in detail:

~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
1)  can't play videos from websites from Firefox

I go to the Ruby on Rails site, and click on the first of the instructional videos, [http://media.rubyonrails.org/video/rails_take2_with_sound.mov](http://media.rubyonrails.org/video/rails_take2_with_sound.mov) 

I have **already installed the xine engine for Kaffeine** using Adept, and also **tried both the Kaffeine and the Kaffeine GStreamer player Engines**, and neither works.

So I will pick the Kaffeine engine and report the symptoms I see there, as they're a bit more informative: I get an error message saying: 

*no plugin found to handle this resource, *

in a window which offers a "details" button. I click it and I see:

[I]xine: couldn't find demux for >http://media.rubyonrails.org/video/rails_take2_with_sound.mov<
input_http: content length = 54364199 bytes
xine: found input plugin : http input plugin[/I]

I also found some references out there about downloading some Win32 codecs. I downloaded a bunch of DLLs in a zipfile with absolutely no indication as to what should be done with them... I deleted those files. 

  Any thoughts? Why can't I just click on a video and see it? Or, more importantly, what can I do so that next time I click on a video on a page, I can see it as soon as it's done downloading?


~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
2) can't listen to Internet radio in either Kaffeine nor amaroK:
When I use either of these applications, it's obvious that they *think* they are playing music. CPU strain goes way up, as does inbound UDP traffic. And I can hear lots of system-event related sounds, like a crashing bottle when an application fails to do something, but no music coming out of my speakers. Ideas?


~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
3) would like FireFox as my default browser: not that I have anything against Konqueror, please! It's just that as a web application developer FireFox is our standard browser at the company, and I know it and its plugins all too well to venture into anything else at this point. 

  I have managed to replace the Konqueror icon on my panel by a FireFox one (well, that wasn't too hard), but still when I click on a link on any other appplication the browser that pops up is Konqueror. Thoughts, suggestions, ideas?


~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
4) is there anything like WinXP's 'minimize all' icon?
It's lame, I know, but I really got used to it. Clicking on each minimize widget of each window when I need to see my desktop fast is annoying. I'm not very familiar with this interface (haven't used KDE in almost ten years!), is there a key combo that does that? A little icon that I could add in my panel would be ideal. Again, any thoughts or suggestions or rants are welcome.


   That's it for now. You'll be hearing more of me as I move all my development work to Linux. Goodbye DreamWeaver! Goodbye Microsoft!

   Thanks a lot to everyone in advance. 

       CESAR

---

### Post by brohan on 2006-01-10
I might suggest to you using [Automatix Kubuntu]("http://ubuntuforums.org/showthread.php?t=105343") for being able to play the internet radio and quicktime. (Quicktime within firefox).
Thats two of your problems solved, because I don't use kubuntu I unforutnatley can't help you with the last two, though I can tell you that those functions exist in GNOME :P

---

### Post by ajgreeny on 2006-01-10
Firefox as your default browser, you need to go to control panel (run kcontrol if not in menus) and set the file associations for htm to firefox.

To minimise all windows why not just use a different desktop of the few you should have available, or simply add the "desktop access" special button available by right clicking on the panel at the bottom of your screen.

---

### Post by cesar on 2006-01-10
[QUOTE=ajgreeny]Firefox as your default browser, you need to go to control panel (run kcontrol if not in menus) and set the file associations for htm to firefox.

To minimise all windows why not just use a different desktop of the few you should have available, or simply add the "desktop access" special button available by right clicking on the panel at the bottom of your screen.[/QUOTE]

Hey thanks for those two tips man! Both very, very handy.

About the problems with video rendering, yah I guess no one here wants to be infringing copyright laws. I'm not... too bad, I'm going to have to switch to windows to see .wmv's ;)

Thanks everybody, this was great. I'm loving Kubuntu.

     CESAR

---

### Post by Billquinn1 on 2006-01-10
automatix is one way to get the playback features you want. You may want to go to:

[https://wiki.ubuntu.com/RestrictedFormats](https://wiki.ubuntu.com/RestrictedFormats)

The instructions for downloading the stuff you need is all there.

---

