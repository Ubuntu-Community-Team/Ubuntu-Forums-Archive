---
title: "Ubuntu desktop using Docker how to mount Synology NAS"
date: 2022-02-20
forum: Desktop Environments
---

### Post by blott0 on 2022-02-20
[COLOR=#232629][FONT=-apple-system]Im following this guide ([https://www.smarthomebeginner.com/docker-home-media-server-2018-basic/](https://www.smarthomebeginner.com/docker-home-media-server-2018-basic/)) using an old laptop as the docker server, in order to migrate the "load" from my synology NAS. This is my first go at using Ubuntu, so im getting my head around it, but I am stuck at how to load my database into radarr from the synology NAS. The setup should work like this. Standalone server: NZBGet would download to the server and unpack into completed folder. Radarr would then scan completed downloads for files and transfer to the NAS once complete. So all folders should be on the server except for the NAS completed database. In my "nano ~/docker/docker-compose.yml" I have[/FONT][/COLOR]
[COLOR=#232629][FONT=-apple-system]Radarr – Movie Download and Management radarr: image: "linuxserver/radarr" container_name: "radarr" volumes:[/FONT][/COLOR]

[LIST]
[*]${USERDIR}/docker/radarr:/config
[*]${USERDIR}/Downloads/completed:/downloads ****Is this the directory to look for when the downloads are completed?*
[*]*# *${USERDIR}/media/movies:/movies ****just hashed this out as it isnt needed*
[*]//< IP of NAS >/volume1/movies ****Assuming this line will be the library but what else do I need to add to make it work?*
[*]"/etc/localtime:/etc/localtime:ro"
[*]${USERDIR}/docker/shared:/shared ports:
[*]"XXXX:XXXX" restart: always environment:
[*]PUID=${PUID}
[*]PGID=${PGID}
[*]TZ=${TZ}
[/LIST]
[COLOR=#232629][FONT=-apple-system]So I just need to figure out how to point radarr to its respective database on the NAS. I have been able to mount the drives and can access them on Ubuntu as a test, but dont know the steps for the dockers. Once I have mapped the right directories, im hoping this will then be reflected in the settings folder of radarr for example, and will show the "drive size" available to be able to confirm this. Then importing should either show up in the list in Radarr- Import Folder or ill have to navigate to the drive via //ip address/ or //server-name/?[/FONT][/COLOR]

---

