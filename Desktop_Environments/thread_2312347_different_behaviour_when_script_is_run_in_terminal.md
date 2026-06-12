---
title: "different behaviour when script is run in terminal or from gnome task bar"
date: 2016-02-03
forum: Desktop Environments
---

### Post by dieter-erich on 2016-02-03
I automated the establishment of a VPN connection with the Big-IP Edge Command Line Client by using this little script:

VAR=true
f5fpc -s -t vpn.univie.ac.at -u username
sleep 3
while $VAR; do
f5fpc --info
sleep 2
if f5fpc --info|grep "Client IPv4"; then
done

When I start it from the gnome terminal it works fine i.e. it asks for the password and on entering it it shows the connection process and finally indicates that the connection is established. The VPN connection remains open on closing the terminal. When I start it from the task bar - where I have added a user-defined application starter - by clicking on the icon, it behaves exactly the same **except from interrupting the VPN connection as soon as the terminal closes**. If I keep it open by adding "$SHELL" at the bottom of the script the connection remains active as long as the terminal remains open. I have no clue where this different behaviour comes from. Thanks for explanations and help!

---

