---
title: "Connecting to servers with Gnome"
date: 2005-04-02
forum: Desktop Environments
---

### Post by drx on 2005-04-02
Hi,

maybe i misunderstand something, but i have the following problems with 
connecting to servers in Gnome (by pressing Cntl+L):

1. To connect to a FTP server seemes to work fine, but any other 
protocol i tried fails. For example, i have a server which doesn't 
support FTP but only SCP. But a scp:// URL will produce an error message 
that this is not a correct location.

2. It is easy to copy, move and change names of files on a FTP 
connection, but when i want to edit something in Gedit remotely, all 
files are suddenly write-protected. Why is that so?

3. Once a connection icon appears on the desktop (seems to be handled 
liek a mounted drive), it is not possible to change any options? Also it 
is not possible to move this icon somewhere, or make a link from it? It 
would be very practical to be able to move it for me, because i need to 
make connections to a lot of servers which would fill my desktop soon. 
(Also the old trick from Windows, to make a "shortcut" to a directory 
from a remote drive, is not working in Gnome, so what you suggest to 
organize server connections in a meaningful way?)

Thanks a lot,
Dragan

---

### Post by shakin on 2005-04-07
[QUOTE=drx]1. To connect to a FTP server seemes to work fine, but any other 
protocol i tried fails. For example, i have a server which doesn't 
support FTP but only SCP. But a scp:// URL will produce an error message 
that this is not a correct location.
[/QUOTE]

You want to use sftp:// instead of scp://. SCP is an older method and I believe even the command line scp program actually uses sftp where possible. Using sftp:// works really well for me.

[QUOTE=drx]
2. It is easy to copy, move and change names of files on a FTP 
connection, but when i want to edit something in Gedit remotely, all 
files are suddenly write-protected. Why is that so?
[/QUOTE]

I don't have that issue. It's surely a permissions problem. Try to chmod 777 a remote text file to see if that makes it work. You may need execute priviledges to remotely edit, but I'm not completely sure.

[QUOTE=drx]
3. Once a connection icon appears on the desktop (seems to be handled 
liek a mounted drive), it is not possible to change any options? Also it 
is not possible to move this icon somewhere, or make a link from it? It 
would be very practical to be able to move it for me, because i need to 
make connections to a lot of servers which would fill my desktop soon. 
(Also the old trick from Windows, to make a "shortcut" to a directory 
from a remote drive, is not working in Gnome, so what you suggest to 
organize server connections in a meaningful way?)[/QUOTE]

I'd like to know how to do this as well. These remote connections seem to be stored as XML files in ~/.nautilus/metafiles and creating a symlink to one of those files opens the XML document in the text editor. There doesn't appear to be a property inside the XML document to tell Nautilus where to place it, but maybe the default is the Desktop and it's possible to add a property to place it somewhere else.

Even with its flaws, Nautilus still beats using the horrible gFTP to open SFTP connections, but isn't quite as good as WinSCP (btw, I created a LinSCP Sourceforge project that I hope to get moving on reasonably soon).

---

