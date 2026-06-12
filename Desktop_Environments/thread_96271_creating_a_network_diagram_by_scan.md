---
title: "creating a network diagram by scan"
date: 2005-11-28
forum: Desktop Environments
---

### Post by sickdude on 2005-11-28
hi all,

im looking for a piece of software that can scan a network and map them into a nice diagram, with pretty pictures.

i googled for it for some time now but i cant seen to find any tool that does this :(

so i was wondering if you guys know anything that does this?

---

### Post by ranf on 2005-11-28
[QUOTE=sickdude]
im looking for a piece of software that can scan a network and map them into a nice diagram, with pretty pictures.
[/QUOTE]
I'm not sure what you mean. Maybe `ettercap' gives you what you want. Maybe not.

---

### Post by sickdude on 2005-11-28
isnt really what i was looking for, but im checking this thing out :)

but what i really mean is this,

a tool that scans a network, and when it finishes it makes a nice network diagram like this [IMG]http://www.hometoys.com/htinews/feb04/articles/emergecore/Network%20Diagram%20A.jpg[/IMG]

---

### Post by Linuturk on 2006-10-15
I'm not as hard to please.

I just want a summary of the hostnames, ip's, and services on my local network.

Something similar to this tool : [http://www.ipswitch.com/Products/WS_Ping/](http://www.ipswitch.com/Products/WS_Ping/)

---

### Post by Linuturk on 2007-01-25
I think your diagram was made in Visio. I don't know of any compliments in the Open Source world besides maybe GIMP.

Anything on my problem?

---

### Post by chipmonk010 on 2007-01-25
i have not seen a program that automatically makes a schematic of a network, i dont think all the detection required is even posbile. for instance my computer doesnt know, and doesnt need to know whether its conected to a single switch or a switch that is uplink to another and another 50 100 1000 switches long.

as for the above poster

netstat may solve part of your request

system >administration>network tools>netstat 

select 'active network services'

can also be run from the command line with
netstat -h 
for a list of options and commands

messing around in ubuntus network tools can get you most of the info you could ever want about a network

if you gather enough information about a network YOU could create a nice schematic with pictures and such but i dont think there is a program to just do all the work

---

### Post by jual_mahal1 on 2007-01-25
You can use [Nomad]("http://netmon.ncl.ac.uk/screenshots/")

If you are so interested in networking software and tools, you can refer to this [useful resource site]("http://www.wiretapped.net/indexes/network-monitoring.html").

---

### Post by Tasu on 2008-03-03
Why not use [LanMap](http://www.parseerror.com/lanmap/)? It's in the repositories, it doesn't auto scans, but once lanuched, it listens for all the network traffic to build a nice svg or png image of the network, to generate the traffic needed by lanmap, I usually scan the network with nmap (somethig like sudo nmap -sS 192.168.0.0/24 works)

---

