---
title: "Gfire Join Game"
date: 2007-10-19
forum: Gaming &amp; Leisure
---

### Post by BitKeeper on 2007-10-19
Hi,

I am using Gfire on Ubuntu 7.10. When I right click on a buddy I can select "Join Game" which then launches the game. But it is like Gfire isn't passing the ip address or port number, so the game just goes to the normal menu. Has anyone had any luck getting gfire to actually join a game based on the ip and port?


My gfire_launch.xml looks like this.

> 
<launchinfo>
        <game id="4097" name="Wolfenstein: Enemy Territory">
                <xqf name="Enemy Territory" modlist="tcetest"/>
                <command>
                        <bin>et +set fs_game tcetest</bin>
                        <dir>/usr/local/games/enemy-territory/</dir>
                        <connect>+connect @ip@:@port@</connect>
                        <launch>@options@ @gamemod@ @connect@</launch>
                </command>
        </game>
</launchinfo>


Thanks.

---

### Post by edglobe on 2007-10-21
when you reach the main menu of ET, open the console (~) and see if you get this message:
```

stdin is not a tty, tty console mode failed

```

if you do, then replace your existing gfire_launch.xml file by this one:

```

<launchinfo>
<game id="4097" name="Wolfenstein: Enemy Territory">
<xqf name="Enemy Territory" />
<command>
<bin>et </bin>
<dir>/usr/local/games/enemy-territory/</dir>
<gamemod>+set fs_game @mod@</gamemod>
<options>+set ttycon 0</options>
<connect>+connect @ip@:@port@</connect>
<launch>@options@ @gamemod@ @connect@</launch>
</command>
</game>
</launchinfo>


```

---

