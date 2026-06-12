---
title: "getting vim to default to xfce4 term rather than xterm"
date: 2013-01-17
forum: Desktop Environments
---

### Post by thaitang on 2013-01-17
It seems when I create a vim.desktop file so that I can right click on files to open them with vim, vim calls xterm, even though I have xfce4-terminal set as my preferred terminal of choice.

Indeed my $TERM env is xterm. But when I right click open-terminal in either Thunar or Nautilus the appropriate default terminal, xfce4 and gnome respectively, opens as expected, and I wonder how can I get that to happen with my vim.desktop file, calling xfce4-terminal instead.

I have tried changing the $TERM env by exporting it in my .bashrc, I but I get an error telling me xfce4-terminal (tried using full path /usr/bin/xfce4-terminal as well) is unknown.

Any ideas how to alter the env $TERM variable to tell it what term emu to use ? Like I mentioned earlier, I have already set xfce4-term as my preferred terminal in settingsManager.

---

