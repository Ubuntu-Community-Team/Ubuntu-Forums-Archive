---
title: "Num lock"
date: 2005-06-15
forum: Desktop Environments
---

### Post by Dave_is_sexy on 2005-06-15
My bios is set to turn numlock on at start-up. Ubuntu kindly turns it off again. Can I tell it not to?

Cheers

---

### Post by desdinova on 2005-06-15
[http://ubuntuguide.org/#numlockx](http://ubuntuguide.org/#numlockx)

"
[Q: How to turn on Num Lock on GNOME startup?]("")

  [list=1]
[*]Read [General Notes]("http://ubuntuguide.org/#generalnotes")
[*]Read [How to add extra repositories?]("http://ubuntuguide.org/#extrarepositories")
[*]sudo apt-get install numlockx
sudo cp /etc/X11/gdm/Init/Default /etc/X11/gdm/Init/Default_backup
sudo gedit /etc/X11/gdm/Init/Default
[*]Find this line     ...
exit 0
[*]Add the following lines above it     if [ -x /usr/bin/numlockx ]; then
  /usr/bin/numlockx on"
fi
[*]Save the edited file ([sample]("http://ubuntuguide.org/sample/Default_numlockx"))
[*]Read [How to restart GNOME without rebooting computer?]("http://ubuntuguide.org/#restartgnomewithoutreboot") 
[/list]

---

### Post by Dave_is_sexy on 2005-06-15
Wow Desdinova you know everything! :D
Did you work on the OS or something?

---

### Post by desdinova on 2005-06-15
Nah - I've been a Linux user for a while so I pick up odd bits here and there - plus its all in Ubuntu Guide so I can't claim credit ;-)

---

