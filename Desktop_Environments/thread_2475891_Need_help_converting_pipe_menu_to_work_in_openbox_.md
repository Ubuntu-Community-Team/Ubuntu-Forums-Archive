---
title: "Need help converting pipe menu to work in openbox menu"
date: 2022-06-11
forum: Desktop Environments
---

### Post by schwim-dandy on 2022-06-11
Hi there neighbors!

I'm in the process of building an Openbox install and one of the things I need to do is to convert my pipemenu that I used in jgmenu to work in openbox's native menu.  When I insert it into the menu, the entire de falls apart with visual bugs and errors.

This script runs in both Debian Buster and Ubuntu 22.04 when using jgmenu.  This menu breaks when trying to run the same pipemenu in openbox's native menu.

the pipemenu:

```

#!/bin/bash

declare -A site1
site1[user]="site1"
site1[remote]="/home/site1"
site1[domain]="site1.com"

declare -A site2
site2[user]="site2"
site2[remote]="/home/site2"
site2[domain]="site2.com"

for u in $HOME/Remote/SSHFS/*
do
  if [ -d $u ]; then
    basename "$u" >/dev/null
    acct="$(basename -- $u)"

    #echo $( eval echo '${'$acct'[remote]}' )
    
    if mountpoint "${HOME}/Remote/SSHFS/${acct}" >/dev/null; then
        printf '%b\n' "unmount $( eval echo '${'$acct'[domain]}' ),fusermount -u /home/schwim/Remote/SSHFS/${acct}"
    else
        printf '%b\n' "mount $( eval echo '${'$acct'[domain]}' ),sshfs -o workaround=rename $( eval echo '${'$acct'[user]}' )@$( eval echo '${'$acct'[domain]}' ):$( eval echo '${'$acct'[remote]}' ) /home/schwim/Remote/SSHFS/${acct}"
    fi

  fi
done
```

I'm inserting it into the menu.xml by:
```

[COLOR=#d4d4d4][FONT=Droid Sans Mono][COLOR=#808080]<[/COLOR][COLOR=#569cd6]separator[/COLOR][COLOR=#808080]/>[/COLOR]
[COLOR=#808080]<[/COLOR][COLOR=#569cd6]menu[/COLOR][COLOR=#9cdcfe]id[/COLOR][COLOR=#d4d4d4]=[/COLOR][COLOR=#ce9178]"ssh-menu"[/COLOR][COLOR=#9cdcfe]label[/COLOR][COLOR=#d4d4d4]=[/COLOR][COLOR=#ce9178]"SSHFS"[/COLOR][COLOR=#9cdcfe]execute[/COLOR][COLOR=#d4d4d4]=[/COLOR][COLOR=#ce9178]"/home/schwim/.scripts/sshfs-pipemenu"[/COLOR][COLOR=#808080]/>[/COLOR]

[COLOR=#808080]<[/COLOR][COLOR=#569cd6]separator[/COLOR][COLOR=#808080]/>[/COLOR]

[/FONT][/COLOR]


```

The error:
[COLOR=#FFFFFF][FONT=&amp][IMG]https://i.imgur.com/NgeLe1x.png?1[/IMG]

D
[/FONT][/COLOR]Does anyone know what I need to change to get that pipemenu to work in Ubuntu 22.04 with Openbox menu?

Thanks for your time!

---

### Post by Holger_Gehrke on 2022-06-11
The output of the pipemenu script has to be XML. See [http://openbox.org/wiki/Help:Menus#Pipe_menus](http://openbox.org/wiki/Help:Menus#Pipe_menus) for details.

Holger

---

### Post by schwim-dandy on 2022-06-11
> **Holger_Gehrke said:**
> The output of the pipemenu script has to be XML. See [http://openbox.org/wiki/Help:Menus#Pipe_menus](http://openbox.org/wiki/Help:Menus#Pipe_menus) for details.

Holger

Ahh, that's very helpful!  So, instead of 

If a remote drive isn't mounted:
> 
mount site1.com,sshfs -o workaround=rename [email]site1@site1.com[/email]:/home/site1 /home/schwim/Remote/SSHFS/site1

and if the remote drive is mounted
> 
unmount site1.com,fusermount -u /home/schwim/Remote/SSHFS/site1


Which has what should show in the menu ahead of the comma and what should occur in the background behind the comma, I need to make it look like:

> 
<menu id="sshfs-menu" label="SSHFS">

     <menu id="site1" label="Site 1">

         <item label="Mount Site 1">

             <action name="Execute"><execute>sshfs -o workaround=rename [email]site1@site1.com[/email]:/home/site1 /home/schwim/Remote/SSHFS/site1</execute></action>

         </item>

         <item label="Mount Site 2">

             <action name="Execute"><execute>unmount site1.com,fusermount -u /home/schwim/Remote/SSHFS/site1</execute></action>

         </item>

     </menu>
</menu>




I'll give this a try right now. Thanks!

---

### Post by schwim-dandy on 2022-06-11
> **Holger_Gehrke said:**
> The output of the pipemenu script has to be XML. See [http://openbox.org/wiki/Help:Menus#Pipe_menus](http://openbox.org/wiki/Help:Menus#Pipe_menus) for details.

Holger

I seem to be continuing to fail at implementing it.  It looks like I've followed the guidelines in the pipe menu wiki but it's showing the same output error.  Here's my output of the pipemenu in the terminal:

```

    <item label="Mount site1.com">
        <action name="Execute"><execute>sshfs -o workaround=rename site1@site1.com:/home/site1 /home/schwim/Remote/SSHFS/site1</execute></action>
    </item>

    <item label="Unmount site2.com">
        <action name="Execute"><execute>fusermount -u /home/schwim/Remote/SSHFS/site2</execute></action>
    </item>

```

And I'm implementing it in the menu like this:

```

  <separator />

  <menu id="sshfs-menu" label="SSHFS" execute="/home/schwim/.scripts/sshfs-pipemenu"/>

  <!-- This requires the presence of the 'obamenu' package to work -->

  <menu id="/Debian" />

  <separator />

  <menu id="applications-menu" label="Applications" execute="/usr/bin/obamenu"/>

  <separator />

  <menu id="preferences" label="Preferences">
    <menu id="conky" label="Conky">
        <item label="Edit">
          <action name="Execute"><execute>code ~/.config/conky/conky.conf</execute></action>

        </item>
...



```

It validates as XML, not sure what I'm doing wrong.

---

### Post by schwim-dandy on 2022-06-11
Got it.  Needed to add at the beginning and end:

```

[COLOR=#d4d4d4][FONT=Droid Sans Mono][COLOR=#d4d4d4] [/COLOR][COLOR=#dcdcaa]printf[/COLOR][COLOR=#d4d4d4] [/COLOR][COLOR=#ce9178]'%b\n'[/COLOR][COLOR=#d4d4d4] [/COLOR][COLOR=#ce9178]"<?xml version=[/COLOR][COLOR=#d7ba7d]\"[/COLOR][COLOR=#ce9178]1.0[/COLOR][COLOR=#d7ba7d]\"[/COLOR][COLOR=#ce9178] encoding=[/COLOR][COLOR=#d7ba7d]\"[/COLOR][COLOR=#ce9178]UTF-8[/COLOR][COLOR=#d7ba7d]\"[/COLOR][COLOR=#ce9178] ?><openbox_pipe_menu xmlns=[/COLOR][COLOR=#d7ba7d]\"[/COLOR][COLOR=#ce9178]http://openbox.org/[/COLOR][COLOR=#d7ba7d]\"[/COLOR][COLOR=#ce9178]  xmlns:xsi=[/COLOR][COLOR=#d7ba7d]\"[/COLOR][COLOR=#ce9178]http://www.w3.org/2001/XMLSchema-instance[/COLOR][COLOR=#d7ba7d]\"[/COLOR][COLOR=#ce9178]  xsi:schemaLocation=[/COLOR][COLOR=#d7ba7d]\"[/COLOR][COLOR=#ce9178]http://openbox.org/[/COLOR][COLOR=#d7ba7d]\"[/COLOR][COLOR=#ce9178] >"[/COLOR]



[/FONT][/COLOR]
...
[COLOR=#d4d4d4][FONT=Droid Sans Mono][COLOR=#dcdcaa]printf[/COLOR][COLOR=#d4d4d4] [/COLOR][COLOR=#ce9178]'%b\n'[/COLOR][COLOR=#d4d4d4] [/COLOR][COLOR=#ce9178]"</openbox_pipe_menu>"[/COLOR]

[/FONT][/COLOR]

```

Remote drives are mounting and unmounting as intended.

Thank you all for your help!

---

