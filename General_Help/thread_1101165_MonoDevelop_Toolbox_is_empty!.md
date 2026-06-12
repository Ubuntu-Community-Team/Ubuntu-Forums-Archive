---
title: "MonoDevelop Toolbox is empty!"
date: 2009-03-20
forum: General Help
---

### Post by FaizanKazi on 2009-03-20
Hi guys, I installed MonoDevelop from Synaptic, and it runs fine, I can compile and publish my asp applications fine on the built in web server (xsp2 - which I had to install separately for some reason, it didnt install automatically with MonoD).

However: I dont know why my ToolBox is empty. I even clicked the "plus" sign button and ticked all the items, specially the System.Web ones which I need for developing my ASP.Net pages.

Tools menu >> Add in manager >> GTK >> GTK # 2.8 is installed and enabled. Also installed and enabled are: 
ASP.NET project support, Project Web references.
Visual Studio .net project support.
C++, CSharp, VB language bindings.
Deployment services core, deployment services for linux.
Visual designer support, Gnome platform support, Text editor, welcome page.
GTK# visual designer, Regex toolkit.

so what did I miss out on?

---

### Post by FaizanKazi on 2009-03-27
bump!! anyone there?

---

### Post by kryptykfysh on 2009-04-11
I am also experiencing this problem.

I tried a suggested solution of deleting the ~/.config/MonoDevelop/Toolbox.xml file while Monodevelop was not running, but this did not resolve the issue.

I'd really appreciate some help with this as it looks like a great tool.

I don't know if this has anything to do with the problem, but when starting the application from a terminal, I get the error below:

> WARNING: Cannot find Mozilla directory containing libgtkembedmoz.so. Some Addins may not be able to function. Please set MOZILLA_FIVE_HOME to your Mozilla directory.

---

### Post by contactpraveen2001 on 2009-04-21
> **FaizanKazi said:**
> Hi guys, I installed MonoDevelop from Synaptic, and it runs fine, I can compile and publish my asp applications fine on the built in web server (xsp2 - which I had to install separately for some reason, it didnt install automatically with MonoD).

However: I dont know why my ToolBox is empty. I even clicked the "plus" sign button and ticked all the items, specially the System.Web ones which I need for developing my ASP.Net pages.

Tools menu >> Add in manager >> GTK >> GTK # 2.8 is installed and enabled. Also installed and enabled are: 
ASP.NET project support, Project Web references.
Visual Studio .net project support.
C++, CSharp, VB language bindings.
Deployment services core, deployment services for linux.
Visual designer support, Gnome platform support, Text editor, welcome page.
GTK# visual designer, Regex toolkit.

so what did I miss out on?
Nevertheless, AspNetEdit can be downloaded as part of the MonoDevelop codebase; it is in the extras/AspNetEdit subdirectory. It can be built against the system MonoDevelop installation by using the configure script (./configure; make; make install). Alternatively it can be hooked into the MonoDevelop build by running the top-level MonoDevelop configure script using a profile that contains AspNetEdit. 

for monre information follow the link 
[http://mono-project.com/AspNetEdit#Installation](http://mono-project.com/AspNetEdit#Installation)

---

### Post by directhex on 2009-04-21
Is the toolbox empty, or is it not being shown? Go to View -> Toolbox to make sure the toolbox is visible

---

### Post by FaizanKazi on 2009-04-21
the toolbox is empty :( 

the toolbox panel has been enabled and shows up on the right hand side of my screen... how sad that i dont have any eggs in my basket :P (or tools in my toolbox as the case might be)


> **directhex said:**
> Is the toolbox empty, or is it not being shown? Go to View -> Toolbox to make sure the toolbox is visible

---

### Post by directhex on 2009-04-21
Odd. Can you post a screenshot?

---

### Post by FaizanKazi on 2009-04-21
I shall try that and get back to you!

meanwhile, a screenshot!

also, I ticked those entries myself for selecting toolbox items, hoping it might make them appear in the toolbox

> **contactpraveen2001 said:**
> Nevertheless, AspNetEdit can be downloaded as part of the MonoDevelop codebase; it is in the extras/AspNetEdit subdirectory. It can be built against the system MonoDevelop installation by using the configure script (./configure; make; make install). Alternatively it can be hooked into the MonoDevelop build by running the top-level MonoDevelop configure script using a profile that contains AspNetEdit. 

for monre information follow the link 
[http://mono-project.com/AspNetEdit#Installation](http://mono-project.com/AspNetEdit#Installation)

---

### Post by directhex on 2009-04-21
***Ah***, ASP.NET

I don't know whether there's any functional GUI designer for ASP.NET in MD right now. Your best bet would be to speak with upstream about it (#monodevelop). The GUI designer right now is pretty much for C#-based GTK# projects

---

### Post by FaizanKazi on 2009-04-22
So I was looking it up, and I think you've found me a solution, but i got kinda lost (more lazy really). I might try it later when i truly figure out which files to download and exactly how to install it, but meanwhile ill stick to virtualizing windows in ubuntu and running visual studio there because it is so much nicer. i dont want to deal with a beta-ish product right now.

> **contactpraveen2001 said:**
> Nevertheless, AspNetEdit can be downloaded as part of the MonoDevelop codebase; it is in the extras/AspNetEdit subdirectory. It can be built against the system MonoDevelop installation by using the configure script (./configure; make; make install). Alternatively it can be hooked into the MonoDevelop build by running the top-level MonoDevelop configure script using a profile that contains AspNetEdit. 

for monre information follow the link 
[http://mono-project.com/AspNetEdit#Installation](http://mono-project.com/AspNetEdit#Installation)

---

### Post by FaizanKazi on 2009-04-23
I think ill stick with virtualizing windows xp in ubuntu and using visual studio for now, because honestly i dont think it gets any better. although monodevelop wouldve been a decent tool for basic testing.

> **directhex said:**
> ***Ah***, ASP.NET

I don't know whether there's any functional GUI designer for ASP.NET in MD right now. Your best bet would be to speak with upstream about it (#monodevelop). The GUI designer right now is pretty much for C#-based GTK# projects

---

