---
title: "Problem with LIRC"
date: 2006-08-10
forum: Desktop Environments
---

### Post by hexion on 2006-08-10
Hello.

I managed (at the end) to compile, install, configure, and run at boot LIRC.

My problem is that I cannot make work irexec and irxevent together.

I need irexec to launch applications, but I need irxevent too to send key command to the applications.

i.e.) I can launch xmms with my avermedia remote control, and stop,start songs... But it has not implemented command lines to fordward 5 seconds the song, it only can be done by sending a "RIGHT ARROW" key to the application. And irexec can't do that (at least it doesn't work for me).


Any suggestions?

Thank you in advance.

---

### Post by Krieg on 2006-09-11
You need this in your ~/.lircrc 

(change the "button" names for the ones you have in your lircd.conf)

```

# XMMS
# Full list of commands can be found in the xmms-lirc readme

begin
  button = fast_forward
  prog = xmms
  config = NEXT
end
begin
  button = play
  prog = xmms
  config = PLAY
end
begin
  button = rewind
  prog = xmms
  config = PREV
end
begin
  button = pause
  prog = xmms
  config = PAUSE
end
begin
  button = stop
  prog = xmms
  config = STOP
end
begin
  button = record
  prog = xmms
  config = SHUFFLE
end
begin
  button = vol-up
  prog = xmms
  config = VOL_UP 10
  repeat = 5
end
begin
  button = vol-down
  prog = xmms
  config = VOL_DOWN 10
  repeat = 5
end
begin
  button = cursor-right
  prog = xmms
  config = FWD 3
  repeat = 5
end
begin
  button = cursor-up
  prog = xmms
  config = FWD 10
  repeat = 5
end
begin
  button = cursor-left
  prog = xmms
  config = BWD 3
  repeat = 5
end
begin
  button = cursor-down
  prog = xmms
  config = BWD 10
  repeat = 5
end
begin
  button = mute
  prog = xmms
  config = MUTE
end
begin
  button = power
  prog = xmms
  config = QUIT
end
begin
  prog = xmms
  button = 1
  config = SELECT 1
end
begin
  prog = xmms
  button = 2
  config = SELECT 2ABC
end
begin
  prog = xmms
  button = 3
  config = SELECT 3DEF
end
begin
  prog = xmms
  button = 4
  config = SELECT 4GHI
end
begin
  prog = xmms
  button = 5
  config = SELECT 5JKL
end
begin
  prog = xmms
  button = 6
  config = SELECT 6MNO
end
begin
  prog = xmms
  button = 7
  config = SELECT 7PQRS
end
begin
  prog = xmms
  button = 8
  config = SELECT 8TUV
end
begin
  prog = xmms
  button = 9
  config = SELECT 9WXYZ
end
begin
  prog = xmms
  button = 0
  config = SELECT 0
end
begin
  prog = xmms
  button = dvd-root_menu
  config = LIST
end
begin
  button = c
  prog = xmms
  config = PLAYLIST_CLEAR
end
begin
  button = launch_setup
  prog = xmms
  config = PLAYLIST_SET /data/ftp/audio/_playlists/my_mega_mix.m3u
end
begin
  button = dvd
  prog = xmms
  config = PLAYLIST_SET /mnt/cdrom
end
begin
  button = tv
  prog = xmms
  config = SLEEP 1
end

```

---

