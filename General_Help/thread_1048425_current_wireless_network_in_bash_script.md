---
title: "current wireless network in bash script"
date: 2009-01-23
forum: General Help
---

### Post by mbeach on 2009-01-23
Hi, 
I'm using synergy at home and work occasionally, with my laptop acting as a client, desktop at each location acting as the server.

Ideally what I would like is a script which would run once the wireless connection is established, connecting to the appropriate ip address depending on the wireless network name.  For now, I'd settle for a method by which to get the current wireless network name in a bash script.  

I currently have a couple of scripts, and I run the right one depending on where I am (syn-connect-home.sh, syn-connect-work1.sh, syn-connect-work2.sh) which basically just call synergyc 192.168.xx.xx depending on where I am, but I'd like to have a single script with a couple of if else statements.  Once I get wireless name part figured out I'll look for the once the connection is up, run this script.

Any thoughts?
mb.

---

### Post by AFarris01 on 2009-11-25
did you ever figure this out? I'm currently seeking an answer to the same question... a few of the wireless networks i connect to regularly require constant activity, and if your level of activity doesn't fit their criteria of 'constant activity' then you get booted off, and have to re-login... which gets annoying when you have to enter in a long username, and even longer password, every 8-10 minutes.  

As a response, I created a script that would basically download the google homepage every 5 min, and pipe it to /dev/null... now I just have to figure out how to get it to run only when I'm connected to this particular wireless network.

EDIT:

I've since rolled my own solution to the issue... I post it here only to help others that may have similar needs.

My solution consists of a simple dirty python script to get the current network information from network-manager, via the 'nm-tool' program. The important info is then extracted via slicing. below is the script, with extensive comments to help understand what it's doing:

```

#!/usr/bin/python
#
# current-network.py -- By Andrew Farris 
#
# This program is intended to return the current connected network name using network-manager's 
# built in tool 'nm-tool'. This program simply slices out the currently connected network name, 
# and prints it out.
# 

import commands

#collect the output from 1 run of 'nm-tool'
nmoutput = commands.getoutput("nm-tool")

# to find the wireless section, find it's heading, which is...
searcher = "Wireless Access Points (* = current AP)"

# slice out the wireless section only (excluding the title above)
slicedoutput = nmoutput[nmoutput.find(searcher)+len(searcher):]

# trim off the beginning of the wireless section, down to the beginning of the default network
trimmed_to_current = slicedoutput[slicedoutput.find("*")+1:]

#print out the slice containing only the current AP
print trimmed_to_current[:trimmed_to_current.find(":")]

```

I'm using this output to control some conditionals in a bash script to execute different other scripts, depending on the network im connected to... where these other scripts set up my environment as desired.

Hope that helps!

---

