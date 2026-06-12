---
title: "Alienarena ad Yo Frankie not running on Ubuntu 9.10"
date: 2010-03-18
forum: Gaming &amp; Leisure
---

### Post by lightningfox on 2010-03-18
Hello

Today I installed two new games on my Ubuntu 9.10

Alien arena from the Ubuntu repos, and a game called Yo Frankie from the website [www.playdeb.net](www.playdeb.net)

The games installed without any problems, but when I try to run the games they don't run.

I disabled Pulseaudio and then tried running them, but they don't run even with Pulseaudio disabled.

When I try running these games from the terminal, I get messages from the terminal.


This is the message I get when I try running Yo Frankie:

```
guessing 'blenderplayer' == '/usr/bin/blenderplayer'
argv[0] = 'blenderplayer'
argv[1] = '/usr/share/yofrankie-bge/levels/start_menu.blend'   , 2
read library: lib //../chars/butterfly.blend
read library: lib //../chars/frankie.blend
read library: lib //../chars/frankie_actions.blend
read library: lib //../chars/bird.blend
read library: lib //momo_actions.blend
read library: lib //frankie_actions.blend
Detected GL_ARB_texture_env_combine
Detected GL_ARB_texture_cube_map
Detected GL_ARB_multitexture
Detected GL_ARB_vertex_program
Detected GL_EXT_separate_specular_color
shaders not supported!
bt_audio_service_open: connect() failed: Connection refused (111)
bt_audio_service_open: connect() failed: Connection refused (111)
bt_audio_service_open: connect() failed: Connection refused (111)
bt_audio_service_open: connect() failed: Connection refused (111)
Segmentation fault
ubuntu@linuxbox:~$ 

```


This is the message I get when I try running Alienarena:

```
using /home/ubuntu/.alien-arena/data1/ for writing
using /home/ubuntu/.alien-arena/arena/ for writing
execing default.cfg
bind <key> [command] : attach a command to a key
Unknown command "wave 4"
couldn't exec config.cfg
Console initialized.

------- sound initialization -------
bt_audio_service_open: connect() failed: Connection refused (111)
bt_audio_service_open: connect() failed: Connection refused (111)
bt_audio_service_open: connect() failed: Connection refused (111)
bt_audio_service_open: connect() failed: Connection refused (111)

```

Please tell me how to fix this.

---

