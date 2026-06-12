---
title: "Force separate per user settings for VPN program?"
date: 2021-08-03
forum: Desktop Environments
---

### Post by Dáire Fagan on 2021-08-03
I have installed Mullvad VPN on Ubuntu 20.04 and noticed that settings are shared across user accounts. I have gone so far as to delete the Mullvad VPN dir in ~/.config/ of the offending account but on reboot I observe the same issue.


Is there some way to force a program to use different settings for each user, and is it not strange it shares the settings by default?

---

### Post by TheFu on 2021-08-03
On Unix systems, networking is shared system-wide, so this is NOT unusual.  Routing tables are system-wide and every VPN that I've seen does something with the routing tables to enable the VPN.

I'm not saying it isn't possible to have per-user setups, iptables does have per-user rule capabilities, but those are almost never used.

---

### Post by Dáire Fagan on 2021-08-04
> **TheFu said:**
> On Unix systems, networking is shared system-wide, so this is NOT unusual. Routing tables are system-wide and every VPN that I've seen does something with the routing tables to enable the VPN.

I'm not saying it isn't possible to have per-user setups, iptables does have per-user rule capabilities, but those are almost never used.

From my brief experience with Nord VPN I think their program may have isolated the settings some how but I cancelled my account so I cannot confirm this.


Today I tried a few different things:

With ```
crontab -u <username> -e
``` for each user I added a single line from the following unique to each:

```

@reboot mullvad relay set location ie dub
@reboot mullvad relay set location uk lon[

```

but both users, even with different crontabs, still connected to the same VPN.

Next I created this script:

```

#!/bin/bash

if [ "$(logname)" = "<username>" ]; then
        mullvad relay set location gb lon
else
        mullvad relay set location ie dub
fi

```

Made executable with:

```
chmod u+x /usr/localbin/mullvadrelay.sh
```

The script itself works when run manually.

I tried getting this to run on login by creating */etc/rc.local* and setting it to read:

```
/usr/localbin/mullvadrelay.sh
```

but this did not work.

I next edited */etc/bash.barshrc* to include the code from the body of the script but discovered this only runs when I open a terminal.

Currently I have the following added to the end of /etc/profile:

```

if [ "$(logname)" = "<username>" ]; then
        mullvad disconnect && mullvad relay set location gb uk && mullvad connect
else
        mullvad disconnect && mullvad relay set location ie dub && mullvad connect
fi

```

The disconnect and connect were initially outside of the if block but did not function properly. They are not entirely necessary but using this connect instead of the Mullvad program's autoconnect prevents duplicate notifications, and it seems cleaner and a good precaution to put a disconnect in place before changing servers.

This works unless I switch to one user and then back to the first, rather than logging out and in, so in dconf to prevent switching I have set:

```

disable-user-switching true 
user-switch-enabled false

```
If there was an option to keep the VPN settings isolated to each user I would prefer to keep the switch functionality but only if I could be certain one account would not leak the connection from one account to the other before being resumed, e.g a website on user1 is connected to a website with VPN1 but while switched to another user, or at some point when resuming user1 requests are sent using VPN2. 

This setup works but I think I must have something wrong as now sometimes when I login my gnome extensions are disabled and I have to turn the parent extension switch on in settings manually. Is there a fix to my solution for the extension issue, or a better way to use a different VPN on each user?

---

### Post by TheFu on 2021-08-04
I strongly suspect when you have 2 VPNs that appear to work concurrently, what is really happening is that 1 VPN is being tunneled inside another VPN.  You can check this using traceroute. The 2nd VPN will show connectivity going through the first VPN, then going to the exit location.

Trying to modify system profiles (profile and bashrc) in /etc/ isn't a good idea.

I think the only way you'll get this working is to use iptables to control the specific routing to/from each exit node using the "-m owner" option. This is non-trivial network stuff. [https://www.cyberciti.biz/tips/block-outgoing-network-access-for-a-single-user-from-my-server-using-iptables.html](https://www.cyberciti.biz/tips/block-outgoing-network-access-for-a-single-user-from-my-server-using-iptables.html) is for a different need, but shows the -m owner option being used.

[https://searchnetworking.techtarget.com/answer/Can-you-have-two-VPN-connections-to-the-same-machine-simultaneously](https://searchnetworking.techtarget.com/answer/Can-you-have-two-VPN-connections-to-the-same-machine-simultaneously) is worth reading. It doesn't have specific commands, just ideas for consideration as you manually setup the connections.  Almost all consumer VPNs use openvpn, which means we don't need to use any specific client provided by the service. We can often control whether split tunneling is allowed. In a corporate environment, organizations that care about security never setup VPNs that allow split tunnels, so that is something else to consider.

---

