---
title: "specifying the storage file size in tcpdump"
date: 2009-01-22
forum: General Help
---

### Post by bhaskar_goel on 2009-01-22
I am trying to get the output of tcpdump in a particular format in a text file of a specified size. Once the file size is reached, another script will store the file in a mysql database.Here is the tcpdump storing script:-

tcpdump -i eth0 -n -q -e | grep -E "IPv4|ARP" | awk -F "[:, >]"  '{ if ($19=="IPv4") print $19 "  " $24 "," $27 "," $22;  else { if ($28=="ff") print $19 "  "$26 "," $34 "," $22 ; else print $19 " " $26 "," $28 "," $22 }    }'

Now i want to store the output in a file until the file reaches a specified size. Any idea how do i get about doing that?

I have tried the -C along with -w option of tcpdump but the file created is filled with illegible contents.

Please help

---

