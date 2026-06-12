---
title: "Gnome Shell. 12.04. Dock extension set to left side?"
date: 2013-03-04
forum: Desktop Environments
---

### Post by Roasted on 2013-03-04
I'm running Ubuntu 12.04.2 with Gnome Shell (3.4 via PPA) and I have the dock extension installed. I'm trying to see if I can make it align to the left side of my screen. I'm having some difficulty doing so based on the limited number of results I found when I Googled. 

One method was to go into dconf-editor and go to org - gnome - shell - extensions - dock and make settings adjustments there. Problem is, there's no "extensions" under "shell". So that alone stopped me dead in my tracks.

On the other hand, I found a gsettings like that looked like a one-liner command to push the dock bar to the left. Instead, it errored out. This sounds like a solution that existed in earlier Gnome Shell/Ubuntu variants.

Is there any way to do this? Or am I stuck?


EDIT - While the "Dock" extension is right justified (hence the reasoning for this post), I found an extension labeled "Dash to Dock" found here:

[https://extensions.gnome.org/extension/307/dash-to-dock/](https://extensions.gnome.org/extension/307/dash-to-dock/)

By default, this one is left justified and works similarly. Nice. I wonder how I could manipulate the other one to work on the left side though? Just for the sake of curiosity, etc...

---

