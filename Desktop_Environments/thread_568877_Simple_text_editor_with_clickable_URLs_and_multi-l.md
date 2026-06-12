---
title: "Simple text editor with clickable URLs and multi-line search and replace?"
date: 2007-10-06
forum: Desktop Environments
---

### Post by Danonymous on 2007-10-06
Does anyone know of a simple text editor that runs in Ubuntu (or Kubuntu, which is actually what I´m using) with two features in particular:  clickable URLs and multi-line search and replace?

Windows has an excellent little text editor with these features:  Metapad 3.51 ([http://www.liquidninja.com/metapad](http://www.liquidninja.com/metapad)).  Metapad allows your search to include a Tab or Newline at the end of a line.  

I´ve tried using Metapad in Wine 0.9.46 but unfortunately Metapad crashes (see my post in the Wine Application Database [[http://appdb.winehq.org]](http://appdb.winehq.org]) for bug details).

I´ve looked at Kwrite (which is what I´m presently using), Kate, gedit, leafpad, etc., but none seem to have both clickable URLs and multi-line search and replace.  (Clickable URLs is on the to-do list for Kate´s developers, and that you can include the beginning of a line as a search item.)  Can anyone point me to a simple editor with these features (or some plug-in for say Kate), without the need to use something big like AbiWord or Open Office?

Thanks.

PS:  Metapad developer Alexander Davidson plans to release the source code under the GNU GPL ([http://www.liquidninja.com/metapad/faq.html](http://www.liquidninja.com/metapad/faq.html)).  It would be great if Alexander did that and someone produced a version for Kubuntu and Ubuntu.

---

### Post by MountainX on 2008-02-04
I'm looking for this too. 

Alternatively, is there any app similar to MS Onelook for Linux?

---

### Post by MountainX on 2008-02-04
I may have one potential solution:
Zim Desktop Wiki
[http://pardus-larus.student.utwente.nl/%7Epardus/projects/zim/index.shtml](http://pardus-larus.student.utwente.nl/%7Epardus/projects/zim/index.shtml)

It's in the repository and can be installed with Synaptics. I'm trying it out now.

For the powerful search & replace feature requirements, I wonder if regex search/replace can be used with Zim Desktop Wiki???

---

### Post by jken146 on 2008-02-04
Mousepad and/or Tea may do what you're looking for.  I can't think of any more likely candidates off the top of my head, but if you type 'text editor' in Add/Remove... you'll surely get a long list.

---

### Post by manimal347 on 2008-02-04
Some of us, especially our server-install and "mothership" Debian users, don't have Synaptic installed, and in any case, most people don't want to wade through the long list of editors, many of them obsolete things like Beaver or Ted. 

Personally, I want a GTK 2.0 text editor that's very simple but allows one to cut and paste, as well as search for text. I currently use Pico running inside Terminal for this. It can be as basic as Microsoft Notepad; the fewer dependencies, the better. Does anyone know of a program like this?

---

### Post by MountainX on 2008-02-04
I am researching several other options for text editors that meet the original two requirements. I'm looking at:
Geany
jEdit
Tea
Leafpad
Rhinote
Amaya
medit
Scribes
SciTE
GVim
and more

Of these, I see two that seem to meet the requirements, although I haven't tested them yet. I'm just reading about them. These two are:
**Geany and Vim**... [UPDATE - Tea doesn't seem to meet the requirements]


**_Geany_**
[http://geany.uvena.de/Main/About](http://geany.uvena.de/Main/About)

It seems to meet the requirements:

1. Context actions may enable opening of URLs:
You can execute a specified command on the current word near the cursor position or an available selection and this word is passed as an argument to this command. 

The passed word can be referred with the wildcard "%s" everywhere in the command, before executing it will be replaced by the current word. For example, the command to open the PHP API documentation would be:

firefox "http://www.php.net/%s"

when executing the command, the %s is substituted by the word near the cursor position or by the current selection. If the cursor is at the word "echo", a browser window will open(assumed your browser is called firefox) and it will open the address: [http://www.php.net/echo](http://www.php.net/echo).

2. You can use regular expressions in the Find and Replace dialogs.

I haven't tried it yet. Here's more info

A more descriptive and great introduction into Geany can be found on [http://www.ubuntunews.info/geany-perfect-programming-ide](http://www.ubuntunews.info/geany-perfect-programming-ide) (thanks to Mateusz Mucha).

Lucas Levin wrote a review about Geany for Opensoft. It can be found at [http://open-soft.org/reviews/programming/ide-geany](http://open-soft.org/reviews/programming/ide-geany).

Jeff Sabarese wrote an article about Geany on Windows. Have a look at [http://novicenotes.com/2008/01/20/best-free-windows-php-ide-text-editor/](http://novicenotes.com/2008/01/20/best-free-windows-php-ide-text-editor/). 
-------------

**_Vim_**

1. Wocvim
      Wocvim is a WoC client for Vim. WoC is a protocol which enables the use of hyperlinks in plain ASCII texts. The links can point to local or remote locations.

2. search & replace


[http://www.faqs.org/faqs/editor-faq/vi/part1/](http://www.faqs.org/faqs/editor-faq/vi/part1/)
How do you do a search and replace?

  Well, there are a few methods.  The simplest is:

    :s/old/new/g 
  But, this only does it on the current line...  So:
    :%s/old/new/g 
  In general: 
    :[range]s/old/new/[cgi] 

  Where [range] is any line range, including line numbers, $ (end of
file), . (current location), % (current file), or just two numbers with
a comma or semicolon between them.  (Or even: .,+5 to mean the next
five lines).


----------

**_Tea_**
[http://tea-editor.sourceforge.net/about.html](http://tea-editor.sourceforge.net/about.html)

1. "Open at cursor"-function for HTML-files and images - this is described as working only for local files

2. Built-in search within files (using multiply charsets) - but only two limited wildcards are supported.

---

### Post by MountainX on 2008-02-05
After some testing, for the requirements of hyperlink support and powerful search/replace, I think Cream (Vim) and Geany are my favorites. Cream will do it all, but the learning curve for getting it to open hyperlinks in a browser is a bit steep. I started another thread for that. There is also a wiki plugin for Vim/Cream that looks interesting.

---

### Post by MountainX on 2008-02-05
Turns out is wasn't too difficult in Cream after all. I followed the instruction below and now I can open URLs in my default browser just by typing Ctrl-Enter when the cursor is on a URL. It works great. Cream is an awesome editor!

Here's the full info from a Cream developer:

I just committed an update that might help, copy this file over yours
of the same name:

 [http://cream.cvs.sourceforge.net/cream/cream/cream-lib.vim](http://cream.cvs.sourceforge.net/cream/cream/cream-lib.vim)

It works if you select a URL and press Ctrl+Enter, or without a
selection as long as the link has a char on either side that Vim does
not define as a filename character by &isfname (:help 'isfname). (The
link format you give above is not valid however. :)
--
Steve Hall

---

### Post by MountainX on 2008-03-27
I'm just reinstalling everything and I realized that one needs to know where to install the updated cream-lib.vim file. Here are the locations.

Here are the Cream file locations I found in Gutsy and Hardy:

/usr/share/vim/cream -- contains addons, docs, and most cream-*.vim scripts

/usr/share/cream -- contains cream-conf.vim and cream-user.vim files

/home/your_user/.cream -- contains my temp docs (being edited), spelldicts, etc.

From my prior conversation with the developer:

> The docs seem to indicate (if I am reading them correctly) that I should put customizations here: /home/myuser/.cream

Correct.

> But I found cream-user.vim here:
> /usr/share/vim/cream

What distribution is this? 
(Ubuntu)
That location is wrong, although some distributions may feel they know better than you (or me!) how to configure defaults.

---

