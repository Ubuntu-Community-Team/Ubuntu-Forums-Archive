---
title: "Parole can't play any video files on upgrade to Xubuntu 23.04"
date: 2023-07-25
forum: Desktop Environments
---

### Post by Saptarshi_Roy on 2023-07-25
[COLOR=#000000][FONT=&quot]Dear Xubuntu Team[/FONT][/COLOR]
[COLOR=#000000][FONT=&quot]Recently, I've upgraded to Xubuntu 23.04 from Xubuntu 22.04 using the 'software updater' tool.[/FONT][/COLOR]
[COLOR=#000000][FONT=&quot]Post upgrading, Parole can't play any video file formats (only the audio is audible while the video is a black screen), and the error observed while playing a video file is as follows:[/FONT][/COLOR]
[COLOR=#000000][FONT=&quot]"Additional software is required. Parole needs Gstreamer element vaapipostproc to play this file. It can be installed automatically".[/FONT][/COLOR]
[COLOR=#000000][FONT=&quot]On choosing the 'Install' option an error is displayed with the message:[/FONT][/COLOR]
[COLOR=#000000][FONT=&quot]"Unable to install missing codecs. No available plugin installer was found."[/FONT][/COLOR]
[COLOR=#000000][FONT=&quot]In Parole's preferences, the 'display' tab has different 'Video Output' options, and all have been tried to no avail.[/FONT][/COLOR]
[COLOR=#000000][FONT=&quot]My computer details are as follows:[/FONT][/COLOR]
[COLOR=#000000][FONT=&quot]Xfce 4.18
GTK version: 3.24.37
Kernel version: 6.2.0-25-generic[/FONT][/COLOR]
[COLOR=#000000][FONT=&quot]Please redress this with the highest priority.[/FONT][/COLOR]
[COLOR=#000000][FONT=&quot]Thank you![/FONT][/COLOR]
[COLOR=#000000][FONT=&quot]--[/FONT][/COLOR]
[COLOR=#000000][FONT=&quot]Kind regards,
Saptarshi Roy[/FONT][/COLOR]

---

### Post by #&amp;thj^% on 2023-07-25
This should solve most of your 2 threads you have now:
```
sudo add-apt-repository universe
```
update sources:
```
sudo apt update && sudo apt install parole
```
Have you added the restricted binary's yet?
```
sudo apt install xubuntu-restricted-addons
```

---

