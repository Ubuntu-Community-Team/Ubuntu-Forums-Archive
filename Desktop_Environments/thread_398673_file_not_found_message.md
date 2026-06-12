---
title: "file not found message"
date: 2007-04-01
forum: Desktop Environments
---

### Post by Chuck_W on 2007-04-01
I hadn't started my Ubuntu machine for a few day so finding that there were updates available was not unexpected. It said that several were ready including Firefox and OpenOffice. When I started the download and install process I got a window that said:

W. Couldn't stat source package list: [http://wine.lowvoice.nl](http://wine.lowvoice.nl) breezy/main packages (vsr/lib/apt/lists/wine.lowvoice.nl_apts_dists_breezy_main_binary_i386_packages) -stat(2 no such file or directory)

I'm not running Wine so I don't understand that reference. The rest of the download and install seemed to go ok. Any ideas as to what it means and if there is a problem I should be concerned about?

---

### Post by dcstar on 2007-04-03
> **Chuck_W said:**
> I hadn't started my Ubuntu machine for a few day so finding that there were updates available was not unexpected. It said that several were ready including Firefox and OpenOffice. When I started the download and install process I got a window that said:

W. Couldn't stat source package list: [http://wine.lowvoice.nl](http://wine.lowvoice.nl) breezy/main packages (vsr/lib/apt/lists/wine.lowvoice.nl_apts_dists_breezy_main_binary_i386_packages) -stat(2 no such file or directory)

I'm not running Wine so I don't understand that reference. The rest of the download and install seemed to go ok. Any ideas as to what it means and if there is a problem I should be concerned about?

That message means you have that repository in your list, and it can no longer be contacted.

Open Synaptic and go into your Repositories and remove it (if you want to).

---

