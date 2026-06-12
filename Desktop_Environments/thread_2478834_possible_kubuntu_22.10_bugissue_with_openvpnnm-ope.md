---
title: "possible kubuntu 22.10 bug/issue with openvpn/nm-openvpn"
date: 2022-09-06
forum: Desktop Environments
---

### Post by 360-dennis on 2022-09-06
Hi, 

I haven't reported a bug for development releases yet, so I'm seeking some guidance if I should report this and where. 

I found a new version of openvpn (2.6) compared to 22.04 (2.5.5), but the nm-openvpn won't connect with my openvpn profile. I found out that the openvpn client does want to connect, but requires --data-cipher with an older cipher that is not currently by default added to the 2.6 client (not that old: AES-256-CBC). Offcourse this should be mitigated on the server side, but this is a closed system from sophos, so that will take time (I will log the incident at sophos support). 

But I found that there is no way to offer a --data-ciper in the .ovpn file (for import by network manager) or to add it to the gui. Which results in not be able to use the network manager in Kubuntu. 

Where should I report this issue? Is it for KDE, Kubuntu or network manager?

---

