---
title: "How to set a timeout for a gnome-vfs ssh connection?"
date: 2007-06-27
forum: Desktop Environments
---

### Post by rivasdiaz on 2007-06-27
I have configured a few SSH connections using Menu Places -> Connect to Servers...

For some servers the connection works OK, and a new nautilus window appears as expected, but in one server, I always get an error dialog saying "Timeout reached". I can connect to the server using the console, so my information is OK and the server is running OK also. The problem is that I need a higher timeout.

I found that with gconf-editor I can edit information about the connection, going to /desktop/gnome/connected_servers/<number> but this area doesn't have a schema and I can't configure the timeout. I was expecting a timeout key in this space but it doesn't exist.

Does anybody knows how I can increase the timeout for an specific gnome-vfs ssh connection?

Thanks in advance.
Rivas

---

