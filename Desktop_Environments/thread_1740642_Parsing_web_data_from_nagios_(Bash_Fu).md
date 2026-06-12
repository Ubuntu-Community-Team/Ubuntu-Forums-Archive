---
title: "Parsing web data from nagios (Bash Fu)"
date: 2011-04-27
forum: Desktop Environments
---

### Post by Grenage on 2011-04-27
_Background_:

We have a system called Skynet, which is basically a bunch of monitoring tools, including Nagios.  What I want to do is output the status of 'critical' processes in conky.  The conky part I'll worry about later (how hard can that be?), but I'm looking for some feedback on how I'm parsing the initial data.  I figure that the simplest way to get the information is to query the cgi, then take what I need from the results...

_Info_:

```
wget -O - "http://user:pass@skynet/nagios/cgi-bin/status.cgi?status.cgi?host=all&servicestatustypes=16&hoststatustypes=3"| grep -i "<TD ALIGN=LEFT valign=center CLASS='statusBGCRITICAL'><A HREF='extinfo.cgi?type=2&host="
```

That basically pipes the web query into grep, and matches a string unique to the lines of data I want:

```
<TD ALIGN=LEFT valign=center CLASS='statusBGCRITICAL'><A HREF='extinfo.cgi?type=2&host=server0&service=Update+Status'>Update Status</A></TD></TR>
<TD ALIGN=LEFT valign=center CLASS='statusBGCRITICAL'><A HREF='extinfo.cgi?type=2&host=server1&service=Update+Status'>Update Status</A></TD></TR>
```

_Desire_:

All I basically want is the server name and the process name, the above example giving server0/server1 and 'update status' as the service.  How would you go about extracting merely these two pieces of information, bearing in mind that the server name and process are variable?

---

### Post by DaithiF on 2011-04-27
Hi, see sed expression below (pipe your data into sed rather than (as i did) use a file)

```
$ cat testfile
<TD ALIGN=LEFT valign=center CLASS='statusBGCRITICAL'><A HREF='extinfo.cgi?type=2&host=server0&service=Update+Status'>Update Status</A></TD></TR>
<TD ALIGN=LEFT valign=center CLASS='statusBGCRITICAL'><A HREF='extinfo.cgi?type=2&host=server1&service=Update+Status'>Update Status</A></TD></TR>

$ sed -r 's/^.*&host=([^&]+)&.*>([^<]+)<.*$/\1\t\2/' testfile
server0 Update Status
server1 Update Status

```

---

### Post by SeijiSensei on 2011-04-27
Pipe it to awk and sed:

```
| awk -F& '{print $2}' | sed 's/host=//g'
```

will return the server name.  It divides the line into fields using the ampersand, returns the second field, then strips off the "host=" part. You can use a similar procedure to return the status.  It's probably easiest to parse the line twice in whatever script you write.

---

### Post by Grenage on 2011-04-27
Thank you, to both of you; that's just the kind of information I was after.

---

