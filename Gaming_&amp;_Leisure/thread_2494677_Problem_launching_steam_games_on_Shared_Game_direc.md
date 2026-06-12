---
title: "Problem launching steam games on Shared Game directory"
date: 2024-01-23
forum: Gaming &amp; Leisure
---

### Post by yaminb on 2024-01-23
I decided to create user accounts for my kids.
I also wanted to give them access to my steam games in case they want to play.

So I created a new folder /home/shared_steam to be used as the steam storage location (where games are installed)
The kids account have their own 'flatpak' install of steam using my account. I just change the storage directory to the same /home/shared_steam
I can still play the games under my account (Works fine)

On the kids login, they can see the games, but when I try and launch a game, i get what look like permission errors.
I tried to chmod 777 the shared_steam dir thinking that would solve it, but no.

Any ideas?


```

ime and disk space.
pressure-vessel-wrap[361]: W: For best results, "/home/shared_steam/steamapps/common/SteamLinuxRuntime_soldier/soldier_platform_0.20231211.70176/files" and "/home/shared_steam/steamapps/common/SteamLinuxRuntime_soldier/var/tmp-BHBUH2/usr" should both be on the same fully-featured Linux filesystem.
pressure-vessel-wrap[361]: W: Unable to create hard link "/home/shared_steam/steamapps/common/SteamLinuxRuntime_soldier/var/tmp-BHBUH2/usr/./lib/valgrind/python3.supp" to "/home/shared_steam/steamapps/common/SteamLinuxRuntime_soldier/soldier_platform_0.20231211.70176/files/./lib/valgrind/python3.supp": Operation not permitted
pressure-vessel-wrap[361]: W: Falling back to copying, but this will take more time and disk space.
pressure-vessel-wrap[361]: W: For best results, "/home/shared_steam/steamapps/common/SteamLinuxRuntime_soldier/soldier_platform_0.20231211.70176/files" and "/home/shared_steam/steamapps/common/SteamLinuxRuntime_soldier/var/tmp-BHBUH2/usr" should both be on the same fully-featured Linux filesystem.
x86_64-linux-gnu-capsule-capture-libs: warning: Dependencies of libnvidia-pkcs11.so.535.154.05 not found, ignoring: Missing dependencies: Could not find "libcrypto.so.1.1" in LD_LIBRARY_PATH "/app/lib/i386-linux-gnu/GL/default/lib:/app/lib/i386-linux-gnu/GL/nvidia-535-154-05/lib:/app/lib32:/app/lib/i386-linux-gnu:/lib64:/app/lib:/usr/lib/x86_64-linux-gnu/GL/default/lib:/usr/lib/x86_64-linux-gnu/GL/nvidia-535-154-05/lib:/usr/lib/x86_64-linux-gnu/openh264/extra:/usr/lib/x86_64-linux-gnu:/home/shared_steam/steamapps/common/Five Nights at Freddy's", ld.so.cache, DT_RUNPATH or fallback /lib:/usr/lib
Proton: Upgrading prefix from 8.0-103 to 6.3-3 (/home/shared_steam/steamapps/compatdata/319510/)
Proton: Removing newer prefix
wineserver: /home/shared_steam/steamapps/compatdata/319510/pfx is not owned by you
wine: '/home/shared_steam/steamapps/compatdata/319510/pfx' is not owned by you
Uploaded AppInterfaceStats to Steam


```

---

### Post by yaminb on 2024-01-23
hmm.

I tried setting some ACLs on it.

Created a group steamusers and added myself and kids to it
Applied an acl recursively so all files are owned by the group steamusers

But it still won't launch under kids account... not sure.

---

### Post by yaminb on 2024-01-25
ok, looks like this is a known wine/proton issue:
[https://github.com/ValveSoftware/Proton/issues/4820](https://github.com/ValveSoftware/Proton/issues/4820)

My solution for now is to have a script that changes the owner of the shared steam library
Pretty clunky. I'll just try and make sure it is set before the kids play. Hopefully this proton issue gets resolved.

> 
#!/bin/bash

#This script is a bit of a clunky workaround for steam
#if using a shared steam storage (/home/shared_steam), you can't use proton with
#multiple users. Wine will complain that some files are not owned by you. This
#occurs even if the user is added to a group that has all permissions.

#looks related to this: [https://github.com/ValveSoftware/Proton/issues/4820](https://github.com/ValveSoftware/Proton/issues/4820)

#START_CONFIGURATION
steam_path="/home/shared_steam"
#END_CONFIGURATION


#first show our steamusers
echo "Listing possible users"
getent group steamusers
echo ""
echo ""
echo "Enter the owner name:"  
read new_owner
echo ""
echo "changing owner to: $new_owner on path $steam_path"

sudo chown -R $new_owner $steam_path




---

