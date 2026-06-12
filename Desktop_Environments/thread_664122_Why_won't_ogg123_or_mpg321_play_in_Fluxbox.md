---
title: "Why won't ogg123 or mpg321 play in Fluxbox?"
date: 2008-01-10
forum: Desktop Environments
---

### Post by TeaSwigger on 2008-01-10
Howdy again folks. I've been running Fluxbox when wishing to run the system lightly on my trusty olde PIII. Recently I've been trying terminal media playback like CPlay, ffmpeg, ogg123 and mpg321. They work fantastically in Konsole in KDE / Kubuntu. Ah but upon trying to play a file in urxvt terminal in Fluxbox, ogg123 and mpg321 both promptly close taking urxvt with 'em. Why? How can I launch and use them in the Fluxbox environment?
:confused:

---

### Post by sumguy231 on 2008-01-10
I don't know why it seems to crash urxvt, but you can run Konsole in Fluxbox as a workaround. This sounds kinda weird, but you might try running urxvt from another terminal and then seeing if there's any output when it crashes.

---

### Post by TeaSwigger on 2008-01-11
> **sumguy231 said:**
> I don't know why it seems to crash urxvt, but you can run Konsole in Fluxbox as a workaround. This sounds kinda weird, but you might try running urxvt from another terminal and then seeing if there's any output when it crashes.

Thanks for the reply. No idea why I didn't think of trying that for error output, but that's why it's so great having fellow linux users to chat with here. I'll go boot into Flux & try that, but thought I'd post that I just tried, in the KDE environment, running ogg123 in urxvt and had no problem! :p brb...

---

### Post by TeaSwigger on 2008-01-11
...back with more to add. Here's how it stacks up:

- ogg123 in Konsole in KDE is a go.

- ogg123 in urxvt in KDE is a go.

- ogg123 in urxvt in Fluxbox is a no-go.

- ogg123 in Konsole in Fluxbox is a go.

- ogg123 in urxvt in Fluxbox *after having ran Konsole* is a go!

In the Fluxbox environment, trying to run ogg123 in urxvt from Konsole results in "file not found" sorts of feedback. Only when spaces and '&' characters are present in the file name! The path must not be passed along with escapes etc. Once Konsole was ran and I then tried ogg123 in urxvt, all was right in the cyber world, even after closing Konsole. 

Why wouldn't the path be passed along right until I start Konsole? Am I correct to zoom in on needing to run some sort of service, like putting something in the Fluxbox startup file? Or...? Count me perplexed. :)

---

