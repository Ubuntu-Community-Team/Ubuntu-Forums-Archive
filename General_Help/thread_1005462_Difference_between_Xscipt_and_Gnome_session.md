---
title: "Difference between Xscipt and Gnome session"
date: 2008-12-08
forum: General Help
---

### Post by zika on 2008-12-08
What is the (inner, deep) difference in these two opitons in Sessions menu on Login screen: X-script and Gnome?

In use I do not see any ... It seems than I have X script as default.

---

### Post by gettinoriginal on 2008-12-10
Hope this helps:  :p

Xscript is a hybrid concept located somewhere between normal propriatary scripting and macro environments, e.g. AutoLisp for AutoCad, and real development languages, e.g. VB(A) or Delphi. The former is usually too propriatary and specifically suited for the application it accompanies, and proper development is usually too hard to cope with for ordinary users. And both usually requires purchase of an additional compiler/development environment. The non-programmer power user falls into the chasm between these two worlds.

Xscript tries to bridge that chasm by adopting a robust XML based format to encapsulate all language logic, while using two simple and generic links to the actual application to evaluate statements and run statements respectively inside the application itself.
What is the Xscript Engine ?

Xscript Engine is an interpreter for Xscript, a neccessary tool to execute the Xscripts. It's the runtime environment for execution of the Xscripts. It reads the Xscript from the file, uses an XML parser to evaluate the Xscript XML content into a memory model (DOM tree), and traverses this DOM tree while executing the individual statements and evaluating the individual expressions as needed.

To do the actual processing, Xscript Engine loads the required Xscript EXtension module, and passes all expressions and commands to this extension for processing. The extension in turn either processes these itself or more probably passes these on to the target application.

Xscript Engine runs in either GUI mode or batch mode. In GUI mode it runs as a normal desktop console application, tracking the progress of every run script. In batch mode it runs minimized, and either terminates or reverts to GUI mode when finished with the given Xscripts. Only the registered version accepts command line parameters, i.e. runs in batch mode.

The console window content is the "log" of the executions. This content can be copied to the clipboard for usage in other applications.

(under development, see online manual for details)
What are Xscript Extensions ?

An Xscript Extension is the bridge between the independent interpreter and the target application. Each extension reveals a fixed interface for Xscript to use, and presumably controls a target application.

Target application control is usually achieved by some sort of inter-process communication, usually either Automation or DDE, but how the extension actually implements the functionality is outside the scope of Xscript itself.

The GNOME project provides two things: The GNOME desktop environment, an intuitive and attractive desktop for users, and the GNOME development platform, an extensive framework for building applications that integrate into the rest of the desktop. You can learn more about how GNOME can work for you in our Why Choose GNOME? page.
GNOME is...
Free

GNOME is Free Software and part of the GNU project, dedicated to giving users and developers the ultimate level of control over their desktops, their software, and their data. Find out more about the GNU project and Free Software at gnu.org.

---

### Post by zika on 2008-12-10
> **gettinoriginal said:**
> Hope this helps:  :p

Xscript is a hybrid concept located somewhere between normal propriatary scripting and macro environments, e.g. AutoLisp for AutoCad, and real development languages, e.g. VB(A) or Delphi. The former is usually too propriatary and specifically suited for the application it accompanies, and proper development is usually too hard to cope with for ordinary users. And both usually requires purchase of an additional compiler/development environment. The non-programmer power user falls into the chasm between these two worlds.

Xscript tries to bridge that chasm by adopting a robust XML based format to encapsulate all language logic, while using two simple and generic links to the actual application to evaluate statements and run statements respectively inside the application itself.
What is the Xscript Engine ?

Xscript Engine is an interpreter for Xscript, a neccessary tool to execute the Xscripts. It's the runtime environment for execution of the Xscripts. It reads the Xscript from the file, uses an XML parser to evaluate the Xscript XML content into a memory model (DOM tree), and traverses this DOM tree while executing the individual statements and evaluating the individual expressions as needed.

To do the actual processing, Xscript Engine loads the required Xscript EXtension module, and passes all expressions and commands to this extension for processing. The extension in turn either processes these itself or more probably passes these on to the target application.

Xscript Engine runs in either GUI mode or batch mode. In GUI mode it runs as a normal desktop console application, tracking the progress of every run script. In batch mode it runs minimized, and either terminates or reverts to GUI mode when finished with the given Xscripts. Only the registered version accepts command line parameters, i.e. runs in batch mode.

The console window content is the "log" of the executions. This content can be copied to the clipboard for usage in other applications.

(under development, see online manual for details)
What are Xscript Extensions ?

An Xscript Extension is the bridge between the independent interpreter and the target application. Each extension reveals a fixed interface for Xscript to use, and presumably controls a target application.

Target application control is usually achieved by some sort of inter-process communication, usually either Automation or DDE, but how the extension actually implements the functionality is outside the scope of Xscript itself.

The GNOME project provides two things: The GNOME desktop environment, an intuitive and attractive desktop for users, and the GNOME development platform, an extensive framework for building applications that integrate into the rest of the desktop. You can learn more about how GNOME can work for you in our Why Choose GNOME? page.
GNOME is...
Free

GNOME is Free Software and part of the GNU project, dedicated to giving users and developers the ultimate level of control over their desktops, their software, and their data. Find out more about the GNU project and Free Software at gnu.org.

Thank You very much for the time and details in Your answer. I will read this post several times just to let the data sink in my 'knowledge-base' ... 

I am using Gnome for now (default was Xscript at the beginning) and get smaller footprint in memory and (I think) better responsivness. To be earnest I do not see much of a difference as an end-user.

Thank You again.

---

### Post by gettinoriginal on 2008-12-10
Glad it could help, don't forget to go to tools and mark this as solved :p

---

