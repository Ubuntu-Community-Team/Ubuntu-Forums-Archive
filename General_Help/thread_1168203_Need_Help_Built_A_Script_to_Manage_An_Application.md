---
title: "Need Help: Built A Script to Manage An Application"
date: 2009-05-23
forum: General Help
---

### Post by jee_bee on 2009-05-23
I need that kind of script for a few different application i would use teamspeak server as example...
i would like to be able to ave a launch script with different option. Im french so start will be start "d" stop "s" restart "r"and quit "q"

> #!/bin/sh

echo  "\033]0;TEAMSPEAK SERVER MANAGER\a"
echo  "Ce terminal peu etre fermer sans interrompre le serveur"
echo  "= "D"émarrer - "A"rrêter - "R"edémarrer - "Q"uiter ="
echo --->get the application Status (if running or not)
ecgo --->if possible the application up-time     

option "d"
          cd /srv/TeamSpeak/tss2_rc2
          ./server_linux

option "s"
          kill $(pgrep server_linux)

option "r" 
          kill $(pgrep server_linux)
          cd /srv/TeamSpeak/tss2_rc2
          ./server_linux

option "q"
          quit

read $
# EoF #

---

