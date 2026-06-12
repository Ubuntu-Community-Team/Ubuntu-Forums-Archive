---
title: "can't print"
date: 2006-05-18
forum: Desktop Environments
---

### Post by helmet on 2006-05-18
hey all

i've redone my setup so as to free up a BUNCH of space...i installed the server of kubuntu, got my samba going again (no problem just copied .conf file back over) and got printers installe and shared and working from my windows computer. i have the CUPS web interface available and BSD printing commands available. if i try to send a test page from the CUPS web interface, nothing happens. it says it worked and the job got completed but nothing happens. well, the laser printer cranks up as if to print but it just winds down again right away. also doing ```
lpr <file>
``` does nothing. what's the prob? i have the foomatic stuff installed and i can print just find from this computer. it' not like it's a major deal, although still would like to be able to do it (and should be able to!)

---

### Post by vidak on 2006-05-18
what does lpq say? Is the printer correctly configured?

---

### Post by utab on 2006-05-18
Dear all,
 
I also have a printer problem

and lpq says 
the printers is ready. 

And the short story is:

I was using a windows network printer till yesterday. Strangely today, I can not use the printer, when I sent a job to the printer, that seems OK, the printer icon appears in the top left pane that I can understand that it is printing, but that icon appears for some seconds and then dissapears. But when the printer was working without problems that icon was showing the same bahaviour. I checked all the connections to my printer, but could not find any defects, So what could be the problem.

I installed the printer from the system administration > printing wizard by supplying the necessary information.

When I use the KDE desktop environment, the behaviour is the same, did somebody change my printer configuration

Regards and thanks

---

### Post by vidak on 2006-05-18
So when you try lpq, you get : 
<printer name> is ready
no entries

and when printing eg. from kghostview, the printer icon appears on the task bar.  Is it possible that the printer is stopped/disabled? (I don't really remember what it is called...)
You can check it under SystemSettings/Printers, I think

---

### Post by utab on 2006-05-18
Exactly

LaserJet-1320 is ready
no entries

I will try that

---

### Post by utab on 2006-05-18
Do u know that as well in KDE

---

### Post by utab on 2006-05-18
Here is my problem

cupsdoprint -P 'LaserJet-1320' -J 'KDE Print Test' -H 'localhost:631' -U 'utab' -o ' multiple-document-handling=separate-documents-uncollated-copies orientation-requested=3' '/usr/share/apps/kdeprint/testprint.ps' : execution failed with message:
server-error-not-accepting-jobs 

Thx

---

### Post by utab on 2006-05-18
If I enable job spoolling optin in the printer settings that gives the above error

---

### Post by vidak on 2006-05-18
that was for KDE. There should be some printer settings in kcontrol - or you can start kprinter from konsole, too... In kprinter you should see your printer's state, which should be 'idle(accepting jobs)'. Is it possible that this option is set to 'stopped'?
Is this a network printer, or is attached directly to your pc?

---

### Post by utab on 2006-05-18
Neteork printer that is connected to a Windows machine.

---

### Post by utab on 2006-05-18
And the status is Idle(Accepting Jobs)

---

### Post by vidak on 2006-05-18
[QUOTE=utab]Neteork printer that is connected to a Windows machine.[/QUOTE]

And what about the printer status?

---

### Post by utab on 2006-05-18
Can this be sth related with the server settings and I am not sure of what is the problem since I was using the printer till 2-3 days ago

---

### Post by vidak on 2006-05-18
can you print from other machines? if you have other OS installed on your pc, does it work with it? 
to be honest, I am running out of ideas... :(

---

### Post by utab on 2006-05-18
I can not print from the windows side as well so

---

### Post by vidak on 2006-05-18
and the other PCs?

---

### Post by ricnmar on 2006-05-18
If the Windows computer cannot print, then the problem is there or with the connection between Windows and the printer.  If Windows won't print, it is unlikely that you can print going through the Windows queue.  

Have you thought about printing directly to the printer?  If the printer is connected directly to the network, try bypassing Windows all together.

ricnmar

---

### Post by randomnote1 on 2006-10-28
if you can't print to a windows machine from another windows machine or any other type of machine, you should try turning off windows firewall.  At least for testing purposes.  Microsoft being the geniouses they are block printing even when file and printer sharing are enabled.

---

