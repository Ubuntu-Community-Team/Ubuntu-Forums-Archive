---
title: "HOWTO: Evince + SyncTeX + vim/emacs/scite/lyx/kile/$EDITOR + forward/backward search"
date: 2011-03-28
forum: Education &amp; Science
---

### Post by Ben___ on 2011-03-28
Hi!

For all of you who didn't get forward/backward search to work. Here is my solution. Thanks to José Aliste who wrote gedit-synctex-plugin:

**Preamble**

[LIST=1]
[*] [Download these files]("http://dud.inf.tu-dresden.de/~ben/evince_synctex.tar.gz")
[*] deflate them to ~/bin (or something within $PATH)
[/LIST]

**Backward Search (Evince &#8594; Editor)**

[LIST=1]
[*] Adopt the first line of »~/bin/evince« (EDITORCMD) to your needs. (run »evince_backward_search« to get help for possible entries)
[*] Compile your .tex File with synctex (»pdflatex -synctex=1 myfile.tex«)
[*] Run »evince myfile.pdf« (The script should run evince_backward_search and evince)
[*] click on some text in evince with »Ctrl+leftclick«
[*] the editor should jump to the corresponding line
[/LIST]

**Forward Search (Editor &#8594; Evince)**

[LIST=1]
[*] you have to tell your editor, to run »evince_forward_search $PDFFILE $LINE $TEXFILE« when pressing some key.
[*] go to some line in your editor and press the key
[*] evince should mark the corresponding line
[/LIST]


in my case (using vim-latexsuite), I wrote in  ~/.vim/after/ftplugin/tex.vim:

```

function! Tex_ForwardSearchLaTeX()
  let cmd = 'evince_forward_search ' . fnamemodify(Tex_GetMainFileName(), ":p:r") .  '.pdf ' . line(".") . ' ' . expand("%:p")
  let output = system(cmd)
endfunction

```
Afterwards you can do forward search in vim with \ls

Ben

edit: thanks to hugmenot, I changed the code according to your comment
edit: changed .vim/ftplugin to .vim/after/ftplugin (thanks to jorges00)

---

### Post by hugmenot on 2011-04-08
I have the following improvements:


```
EDITORCMD="vim --servername 'VIM' --remote-silent '+%l<Enter>:match Search /\%%ll/' %f"

```

Make it remote-silent and highlight the line it jumped to. (in bin/evince, ignore vim --servername 'VIM')


And 

```
function! Tex_ForwardSearchLaTeX()
	let commandline = 'evince_forward_search '. fnamemodify(Tex_GetMainFileName(), ":p:r") .'.pdf '. line(".") .' '. expand("%:p")
	let output = system(commandline)
endfunction
```

Use system() to make it silent and not prompt the user.

---

### Post by hugmenot on 2011-04-08
Once we have sorted this out properly we should post it [here]("http://tex.stackexchange.com/questions/2941/how-to-setup-synctex-with-vim-pdflatex-and-an-open-source-pdf-viewer-under-linux")

---

### Post by jorges00 on 2011-05-04
Was this solution tested on gnome-2.32 or in gnome-3. I've read [here]("http://jlebl.wordpress.com/2011/01/13/vim-evince-and-forward-and-backward-latex-synctex-search/") that the dbus interface has changed in gnome-3, and I get some messages about function on_sync_source() taking exactly 3 arguments, but being given 4. Could this be the source of the error?

The solution in the link above works for me under gnome-3, but the one given here seems much cleaner, i.e. don't have to manually launch a process, etc.

Thanks in advance,

jorges

---

### Post by jorges00 on 2011-05-05
> **jorges00 said:**
> Was this solution tested on gnome-2.32 or in gnome-3. I've read [here]("http://jlebl.wordpress.com/2011/01/13/vim-evince-and-forward-and-backward-latex-synctex-search/") that the dbus interface has changed in gnome-3, and I get some messages about function on_sync_source() taking exactly 3 arguments, but being given 4. Could this be the source of the error?

The solution in the link above works for me under gnome-3, but the one given here seems much cleaner, i.e. don't have to manually launch a process, etc.

Thanks in advance,

jorges

I found the answer myself: The solution posted above needs some changes in order to work with gnome-3, as it seems the dbus interface changed.

Below there's a diff of the required changes:

```
diff -urN evince_synctex/evince_backward_search evince_synctex.mod/evince_backward_search
--- evince_synctex/evince_backward_search       2011-04-26 03:20:28.000000000 -0300
+++ evince_synctex.mod/evince_backward_search   2011-05-05 00:57:11.848306440 -0300
@@ -104,14 +104,14 @@
             if self._log:
                 self._log.debug("GetWindowList returned empty list")

-    def on_sync_source(self, input_file, source_link):
+    def on_sync_source(self, input_file, source_link, time):
         print input_file + ":" + str(source_link[0])
         cmd = re.sub("%f",input_file,self.editor)
         cmd = re.sub("%l",str(source_link[0]), cmd)
         print cmd
         subprocess.call(cmd, shell=True)
         if self.source_handler is not None:
-            self.source_handler(input_file, source_link)
+            self.source_handler(input_file, source_link, time)


 ## This file offers backward search in any editor.
diff -urN evince_synctex/evince_forward_search evince_synctex.mod/evince_forward_search
--- evince_synctex/evince_forward_search        2011-03-23 18:53:05.000000000 -0300
+++ evince_synctex.mod/evince_forward_search    2011-05-05 00:57:21.511639938 -0300
@@ -44,4 +44,4 @@
 except dbus.DBusException:
     print_exc()

-window.SyncView(tex_file, (line_number,1), dbus_interface="org.gnome.evince.Window")
+window.SyncView(tex_file, (line_number,1), 0, dbus_interface="org.gnome.evince.Window")
```

jorges

---

### Post by jorges00 on 2011-05-05
> **hugmenot said:**
> I have the following improvements:


```
EDITORCMD="vim --servername 'VIM' --remote-silent '+%l<Enter>:match Search /\%%ll/' %f"

```



Would someone explain the pattern used to highlight the line in vim? I mean the "\%%ll" pattern. I can't find the information within vim's docs, and google searches are useless as it ignores special characters.

Thanks

jorges

---

### Post by hugmenot on 2011-05-05
> **jorges00 said:**
> 
```
EDITORCMD="vim --servername 'VIM' --remote-silent '+%l<Enter>:match Search /\%%ll/' %f"
```
Would someone explain the pattern used to highlight the line in vim? I mean the "\%%ll" pattern. I can't find the information within vim's docs, and google searches are useless as it ignores special characters.


Yes. The regex pattern /\%50l/ would match the whole line 50, check :help /ordinary-atom. The awkward part come in where %l is also the replacement variable that Evince needs to substitute the line number. 

[LIST]
[*]+%l &#8594; go to line %l  (and Enter to do it)
[*]:match Search /\%%ll/' &#8594; highlight line %l
[*]%f &#8594; load file %f
[/LIST]

---

### Post by jorges00 on 2011-05-05
> **hugmenot said:**
> Yes. The regex pattern /\%50l/ would match the whole line 50, check :help /ordinary-atom. The awkward part come in where %l is also the replacement variable that Evince needs to substitute the line number. 

[LIST]
[*]+%l &#8594; go to line %l  (and Enter to do it)
[*]:match Search /\%%ll/' &#8594; highlight line %l
[*]%f &#8594; load file %f
[/LIST]

Ahh! that's why I couldn't find the pattern in the vim docs. Thanks for clarifying it!

jorges

---

### Post by ezitoc on 2011-05-15
Hi Ben!
I also use the vim-latexsuite package (just installed today) and i can't do forward search (nor backward). I added the lines you mentioned to the tex.vim file but i get the same result as if i'd use my old tex.vim file. I'm kind of newbie at all this, so if you need more information please ask. I don't know if it is relevant information, but i use debian squeeze.
Thanks!

---

### Post by jorges00 on 2011-05-15
> **ezitoc said:**
> Hi Ben!
I also use the vim-latexsuite package (just installed today) and i can't do forward search (nor backward). I added the lines you mentioned to the tex.vim file but i get the same result as if i'd use my old tex.vim file. I'm kind of newbie at all this, so if you need more information please ask. I don't know if it is relevant information, but i use debian squeeze.
Thanks!

The same happened to me. What I did to solve it was to define the function suggested by Ben in the ~/.vim/after/ftplugin/tex.vim, and then it did take precedence over the function defined by latex-suite.

jorges

---

### Post by tensecor on 2011-05-19
This dose not work when the tex file name contains space or some of its parent directories' name contains space.

> **Ben___ said:**
> Hi!

For all of you who didn't get forward/backward search to work. Here is my solution. Thanks to José Aliste who wrote gedit-synctex-plugin:

**Preamble**

[LIST=1]
[*] [Download these files]("http://dud.inf.tu-dresden.de/~ben/evince_synctex.tar.gz")
[*] deflate them to ~/bin (or something within $PATH)
[/LIST]

**Backward Search (Evince &#8594; Editor)**

[LIST=1]
[*] Adopt the first line of »~/bin/evince« (EDITORCMD) to your needs. (run »evince_backward_search« to get help for possible entries)
[*] Compile your .tex File with synctex (»pdflatex -synctex=1 myfile.tex«)
[*] Run »evince myfile.pdf« (The script should run evince_backward_search and evince)
[*] click on some text in evince with »Ctrl+leftclick«
[*] the editor should jump to the corresponding line
[/LIST]

**Forward Search (Editor &#8594; Evince)**

[LIST=1]
[*] you have to tell your editor, to run »evince_forward_search $PDFFILE $LINE $TEXFILE« when pressing some key.
[*] go to some line in your editor and press the key
[*] evince should mark the corresponding line
[/LIST]


in my case (using vim-latexsuite), I wrote in  ~/.vim/ftplugin/tex.vim:

```

function! Tex_ForwardSearchLaTeX()
  let cmd = 'evince_forward_search ' . fnamemodify(Tex_GetMainFileName(), ":p:r") .  '.pdf ' . line(".") . ' ' . expand("%:p")
  let output = system(cmd)
endfunction

```
Afterwards you can do forward search in vim with \ls

Ben

edit: thanks to hugmenot, I changed the code according to your comment

---

### Post by florenzen on 2011-07-04
Hello,

I have adapted ben's Python code to Emacs lisp for forward search using AUCTeX.

The following code in .emacs does the job if the D-bus support of Emacs is available. Pressing C-c C-v will jump to the output line corresponding to the current line in the source buffer. A new Evince window is started if the document is not yet opened.

```

;; Forward/inverse search with evince using D-bus.
(if (require 'dbus "dbus" t)
    (progn
      ;; Forward search.
      ;; Adapted from http://dud.inf.tu-dresden.de/~ben/evince_synctex.tar.gz
      (defun auctex-evince-forward-sync (pdffile texfile line)
        (let ((dbus-name
           (dbus-call-method :session
                     "org.gnome.evince.Daemon"  ; service
                     "/org/gnome/evince/Daemon" ; path
                     "org.gnome.evince.Daemon"  ; interface
                     "FindDocument"
                     (concat "file://" pdffile)
                     t     ; Open a new window if the file is not opened.
                     )))
          (dbus-call-method :session
                dbus-name
                "/org/gnome/evince/Window/0"
                "org.gnome.evince.Window"
                "SyncView"
                texfile
                (list :struct :int32 line :int32 1))))

      (defun auctex-evince-view ()
        (let ((pdf (file-truename (concat default-directory
                          (TeX-master-file (TeX-output-extension)))))
          (tex (buffer-file-name))
          (line (line-number-at-pos)))
          (auctex-evince-forward-sync pdf tex line)))

      ;; New view entry: Evince via D-bus.
      (add-to-list 'TeX-view-program-list
               '("EvinceDbus" auctex-evince-view))

      ;; Prepend Evince via D-bus to program selection list
      ;; overriding other settings for PDF viewing.
      (add-to-list 'TeX-view-program-selection
               '(output-pdf "EvinceDbus"))

      ;; Inverse search.
      ;; Adapted from: http://www.mail-archive.com/auctex@gnu.org/msg04175.html 
      (defun auctex-evince-inverse-sync (file linecol)
        (let ((buf (get-buffer (file-name-nondirectory file)))
          (line (car linecol))
          (col (cadr linecol)))
          (if (null buf)
          (message "Sorry, %s is not opened..." file)
        (switch-to-buffer buf)
        (goto-line (car linecol))
        (unless (= col -1)
          (move-to-column col)))))

      (dbus-register-signal
       :session nil "/org/gnome/evince/Window/0"
       "org.gnome.evince.Window" "SyncSource"
       'auctex-evince-inverse-sync)))

```Note: the inverse search code is by Tassilo Horn and I included it for completeness.

Regards,

Florian

---

### Post by heito on 2011-07-27
The backward search script works great for me, if I call instead of evince our evince script (let call it evince-sync). However if I start it like 

evince-sync -p 10 file.pdf

backward search doesn't work (it just does nothing). Any idea how to fix this? I guess it should be a minor change in your code...

Using the -p option is the standard forward search method from emacs. I tried to use your method for forward search, but it didn't work.

---

### Post by Repabil on 2011-10-20
> **florenzen said:**
> The following code in .emacs does the job if the D-bus support of Emacs is available. Pressing C-c C-v will jump to the output line corresponding to the current line in the source buffer. A new Evince window is started if the document is not yet opened.

I tried your code but Emacs freezes when I do C-c C-v (it goes unresponsive).

---

### Post by florenzen on 2011-10-31
The new Evince in Ubuntu 11.10 requires two slight changes in the Emacs Lisp code to work properly. Here is the patch:

```

--- emacs       (revision 10195)
+++ emacs       (local)
@@ -272,22 +272,27 @@
          ;; Forward search.
          ;; Adapted from http://dud.inf.tu-dresden.de/~ben/evince_synctex.tar.gz
          (defun auctex-evince-forward-sync (pdffile texfile line)
-           (let ((dbus-name
-                  (dbus-call-method :session
-                                    "org.gnome.evince.Daemon"  ; service
-                                    "/org/gnome/evince/Daemon" ; path
-                                    "org.gnome.evince.Daemon"  ; interface
-                                    "FindDocument"
-                                    (concat "file://" pdffile)
-                                    t  ; Open a new window if the file is not opened.
-                                    )))
+           (let* ((dbus-name
+                   (dbus-call-method :session
+                                     "org.gnome.evince.Daemon"  ; service
+                                     "/org/gnome/evince/Daemon" ; path
+                                     "org.gnome.evince.Daemon"  ; interface
+                                     "FindDocument"
+                                     (concat "file://" pdffile)
+                                     t         ; Open a new window if the file is not opened.
+                                     ))
+                  (time (current-time))
+                  (high (car time))
+                  (low (cadr time))
+                  (timestamp (+ (* high (expt 2 16)) low)))
              (dbus-call-method :session
                                dbus-name
                                "/org/gnome/evince/Window/0"
                                "org.gnome.evince.Window"
                                "SyncView"
                                texfile
-                               (list :struct :int32 line :int32 1))))
+                               (list :struct :int32 line :int32 1)
+                               timestamp)))
 
          (defun auctex-evince-view ()
            (let ((pdf (file-truename (concat default-directory
@@ -307,7 +312,7 @@
 
          ;; Inverse search.
          ;; Adapted from: http://www.mail-archive.com/auctex@gnu.org/msg04175.html 
-         (defun auctex-evince-inverse-sync (file linecol)
+         (defun auctex-evince-inverse-sync (file linecol timestamp)
            (let ((buf (get-buffer (file-name-nondirectory file)))
                  (line (car linecol))
                  (col (cadr linecol)))

```

Regards,

Florian

---

### Post by Repabil on 2011-11-01
Thanks. That works on smaller files. But when I try it on larger files Emacs freezes after I do C-c C-v or Ctrl+click.

In *Messages*:

> let*: D-Bus error: "Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken." [2 times]

---

### Post by ddrake_ on 2012-04-03
> **florenzen said:**
> The new Evince in Ubuntu 11.10 requires two slight changes in the Emacs Lisp code to work properly. Here is the patch:

I incorporated your patch into the above code; it's now at  [https://gist.github.com/2297447](https://gist.github.com/2297447). I also fixed a problem with symlinks; SyncTeX follows them and uses that for the filenames in the synctex.gz file (see [http://tex.stackexchange.com/questions/25578/why-is-synctex-in-tl-2011-so-fussy-about-filenames](http://tex.stackexchange.com/questions/25578/why-is-synctex-in-tl-2011-so-fussy-about-filenames)), but buffer-file-name in Emacs may not. So I added a "file-truename" to fix that. You'll need to use the TEXINPUTS trick from the tex.SE question, though.

---

### Post by Bausparfuchs on 2012-04-19
I just want to share my experience with getting the whole thing running using kile with evince. I also would be very pleased if anyone could help me to get forward search working.

My distro: Ubuntu 11.10 "Oneiric"
My dbus version: 1.4.14-1ubuntu1
My kile version: 2.1.0
My evince version: 3.2.1

First I got the backward search running by using the file "evince_backward search", modified as shown below:

```

import dbus, subprocess, time, re

RUNNING, CLOSED = range(2)

EV_DAEMON_PATH = "/org/gnome/evince/Daemon" 
EV_DAEMON_NAME = "org.gnome.evince.Daemon" 
EV_DAEMON_IFACE = "org.gnome.evince.Daemon"

EVINCE_PATH = "/org/gnome/evince/Evince" 
EVINCE_IFACE = "org.gnome.evince.Application"

EV_WINDOW_IFACE = "org.gnome.evince.Window"



class EvinceWindowProxy:
    """A DBUS proxy for an Evince Window."""
    daemon = None
    bus = None

    def __init__(self, uri, editor, spawn = False, logger = None):
        self._log = logger
        self.uri = uri
        self.editor = editor
        self.status = CLOSED
        self.source_handler = None
        self.dbus_name = ''
        self._handler = None
        try:
            if EvinceWindowProxy.bus is None:
                EvinceWindowProxy.bus = dbus.SessionBus()

            if EvinceWindowProxy.daemon is None:
                EvinceWindowProxy.daemon = EvinceWindowProxy.bus.get_object(EV_DAEMON_NAME,
                                                EV_DAEMON_PATH,
                                                follow_name_owner_changes=True)
            EvinceWindowProxy.bus.add_signal_receiver(self._on_doc_loaded, signal_name="DocumentLoaded",
                                                      dbus_interface = EV_WINDOW_IFACE,
                                                      sender_keyword='sender')
            self._get_dbus_name(False)

        except dbus.DBusException:
            if self._log:
                self._log.debug("Could not connect to the Evince Daemon")

    def _on_doc_loaded(self, uri, **keyargs):
        if uri == self.uri and self._handler is None:
            self.handle_find_document_reply(keyargs['sender'])
        
    def _get_dbus_name(self, spawn):
        EvinceWindowProxy.daemon.FindDocument(self.uri,spawn,
                     reply_handler=self.handle_find_document_reply,
                     error_handler=self.handle_find_document_error,
                     dbus_interface = EV_DAEMON_IFACE)

    def handle_find_document_error(self, error):
        if self._log:
            self._log.debug("FindDocument DBus call has failed")

    def handle_find_document_reply(self, evince_name):
        if self._handler is not None:
            handler = self._handler
        else:
            handler = self.handle_get_window_list_reply
        if evince_name != '':
            self.dbus_name = evince_name
            self.status = RUNNING
            self.evince = EvinceWindowProxy.bus.get_object(self.dbus_name, EVINCE_PATH)
            self.evince.GetWindowList(dbus_interface = EVINCE_IFACE,
                          reply_handler = handler,
                          error_handler = self.handle_get_window_list_error)

    def handle_get_window_list_error (self, e):
        if self._log:
            self._log.debug("GetWindowList DBus call has failed")

    def handle_get_window_list_reply (self, window_list):
        if len(window_list) > 0:
            window_obj = EvinceWindowProxy.bus.get_object(self.dbus_name, window_list[0])
            self.window = dbus.Interface(window_obj,EV_WINDOW_IFACE)
            self.window.connect_to_signal("SyncSource", self.on_sync_source)
        else:
            #That should never happen.

            if self._log:
                self._log.debug("GetWindowList returned empty list")

    def on_sync_source(self,input_file,source_link,time):
	
	fake_input = re.sub("file://",'',input_file)
	cmd = re.sub("%f",fake_input,self.editor)
	cmd = re.sub("%l",str(source_link[0]), cmd)
	print cmd
	subprocess.call(cmd, shell=True)
        if self.source_handler is not None:
            self.source_handler(input_file, source_link)

## This file offers backward search in any editor.
##  evince_dbus pdf_file line_source input_file
if __name__ == '__main__':
    import dbus.mainloop.glib, gobject, glib, sys, os

    def print_usage():
        print """Usage:
  evince_backward_search pdf_file "editorcmd %f %l"'
    %f ... TeX-file to load
    %l ... line to jump to E.g.:
  evince_backward_search somepdf.pdf "gvim --servername somepdf --remote-silent '+%l<Enter>' %f"
  evince_backward_search somepdf.pdf "emacsclient -a emacs --no-wait +%l %f"
  evince_backward_search somepdf.pdf "scite %f '-goto:%l'"
  evince_backward_search somepdf.pdf "lyxclient -g %f %l"
  evince_backward_search somepdf.pdf "kate --use --line %l"
  evince_backward_search somepdf.pdf "kile --line %l" """
        sys.exit(1)

    if len(sys.argv)!=3:
        print_usage()

    pdf_file = os.path.abspath(sys.argv[1])

    if not os.path.isfile(pdf_file):
        print_usage()

    dbus.mainloop.glib.DBusGMainLoop(set_as_default=True)
    
    a = EvinceWindowProxy('file://' + pdf_file, sys.argv[2] ,True)
 
    loop = gobject.MainLoop()
    loop.run()



```

And calling it via "ViewPDF" in kile using the command: /usr/local/bin/evince '%target', where the Editor command in the script "evince" has to look like this:

```
EDITORCMD="kile --line %l %f"
```

That works very well.

Secondly I had to find a way to call the script "evince_forward_search" with the parameters described in the first post from kile.

I did that by writing that script below:

```
#!/bin/bash
#this is 'forwardsearch.sh'
#line

LINE=$(echo $1 | cut -d : -f 3 | cut -d / -f 1)

#echo $LINE

#pdf

PDFFILE=$(echo $1 | cut -d : -f 2 | cut -d \# -f 1)

#texfile

TEXFILE=$(echo $1 | cut -d : -f 3 | cut -d / -f 2-8 | sed -e 's/home/\/home/g')


echo "evince_forward_search" $PDFFILE $LINE $TEXFILE
evince_forward_search $PDFFILE $LINE $TEXFILE

```

When invoked from kile using the command 
```
forwardsearch.sh '%absolute_target'
```
that script calls the programm "evince_forward_search" with the described parameters.

Due to upcoming dbus errors I had to change the script "evince_backward_search" slightly as described before in this thread:

```
-window.SyncView(tex_file, (line_number,1), dbus_interface="org.gnome.evince.Window")
+window.SyncView(tex_file, (line_number,1), 0, dbus_interface="org.gnome.evince.Window")
```

After that change, the script runs without any error but does not highlight anything in the pdf. The pdf just gets opened. Maybe someone can help me out.

Thx

---

### Post by Ottokraftstoff on 2012-06-29
Hi Guys.
I just wanted to tell the world out there how I got the synctex-script working with evince and geany, because your posts were very helpful for me and I hope my experiences can help other people.

 My configuration is  
evince 3.4.0
geany 0.21
Ubuntu 12.04 64Bit with Unity
Tex Live 2009

First, I downloaded the script and deflated the files to ~/bin.

Secondly, I modified the script files as suggested by jorges00 in Post #5 to get them working with the newer dbus interface (what ever that is).

Thirdly, I told geany to compile my document with the the synctex option by defining the following custom build command:
```
pdflatex %f && bibtex %e && pdflatex %f && pdflatex  -synctex=1  %f
```Then, to get backward search (Evince &#8594; Editor**) **running, I modified the second line of evince.sh as follows:
```

EDITORCMD="geany -l %l %f &"

```Please note that I added a "&" at the end. Without that I had the following problem: When I CTRL+clicked in the pdf, geany opened the correct file at the correct line. But when I clicked for the second time, nothing happened and geany was somehow frozen until I closed it. Then a new instance popped up and showed the line where I had clicked the second time.
I do not know if that extra "&" is an appropriate solution, but it works for me.

I have not managed to get forward search (Editor &#8594; Evince**) **running with geany. You could tell geany to execute commands or run scripts. But as far as i understand the internet, there is no possibility of handing over the current line number from geany to a script. The reason is that a wildcard for the linenumber has not been implemented in geany yet.

However, I find backward search much more important than forward search, so I am really happy now with my setup. In Fact, the synctex-evince script and the advice from this forum to get it working enhanced the magnificence __of my workflow by approximately 200%. Thank your for that.
Though, if anybody knows how to make forward search possible with geany, please let me know.

---

### Post by giopao314 on 2012-08-03
Hi all,

I'm trying to have backward search in Lyx using evince and the scripts of this forum.

My configuration is:
Ubuntu 12.04 64bit with Unity
evince 3.4.0
Lyx 2.02

Forward search (Lyx -> evince) works great from Lyx 2.0 on, so my only problem is backward search using evince.

I followed the steps suggested by [Ottokraftstoff:]("http://ubuntuforums.org/member.php?u=1688479")

First, I downloaded the script and deflated the files to ~/bin.

Secondly, I modified the script files as suggested by jorges00 in Post  #5 to get them working with the newer dbus interface (what ever that  is).

Third, to get backward search (Evince &#8594; Lyx**) **running, I modified the second line of evince.sh as suggested in evince_backward_search, i.e.:

```
EDITORCMD="lyxclient -g %f %l &"
```

I tried with and without the & at the end, but nothing change.

Using Ctrl+click on evince nothing happen.

Please, can someone help me in some way?

Many thanks in advance!

---

### Post by marciano on 2012-09-24
Grrr! I got this to work beautifully on 12.04 with Sublime Text 2... but things have stopped working on 12.10 beta1 with today's updates ##@$@#)($*!!!

evince_forward_search now errors out upon calling "print_exc()", which means that the dbus interface or somehting like it must have changed yet again! Any wisdom to be offered?

**Edit:** scratch the above. The problem is that the scripts do not seem to support file names with spaces. I'll see if I can fix this. More info:

- The exception thrown is as follows:

```

Traceback (most recent call last):
  File "/home/<OMITTED>/.config/sublime-text-2/Packages/LaTeXTools/evince/evince_forward_search", line 44, in <module>
    dbus_name = daemon.FindDocument('file://' + pdf_file, True, dbus_interface = "org.gnome.evince.Daemon")
  File "/usr/lib/python2.7/dist-packages/dbus/proxies.py", line 70, in __call__
    return self._proxy_method(*args, **keywords)
  File "/usr/lib/python2.7/dist-packages/dbus/proxies.py", line 145, in __call__
    **keywords)
  File "/usr/lib/python2.7/dist-packages/dbus/connection.py", line 651, in call_blocking
    message, timeout)
dbus.exceptions.DBusException: org.freedesktop.DBus.Error.NoReply: Message did not receive a reply (timeout by message bus)

```

- What fails is the call to FindDocument.
- Quoting the file name in the call to FindDocument does not work.

If anyone has any advice, it's very welcome!

---

### Post by marciano on 2012-09-24
OK, I solved my own problem :-)

The evince_{forward,backward}_search scripts do not seem to handle file names with spaces. The problem is that the Evince FindDocument call expects an URI for the file name, with spaces replaced with "%20". If you pass a file name with non-encoded spaces, the call throws an exception. On the other hand, SyncTeX handles file names with spaces just fine, but a consequence of this is that if you replace spaces with "%20" in the name of the TeX file, syncing will fail (most likely, your editor will open a new window or tab with a new file name).

To fix this, you need the following changes:

1. in evince_forward_search, replace the line that says

```

pdf_file = os.path.abspath(sys.argv[1])

```

with 

```

pdf_file = os.path.abspath(sys.argv[1]).replace(" ", "%20")

```

2. in evince_backward_search, method __init__(), replace the line

```

self.uri = uri

```

with

```

self.uri = uri.replace(" ", "%20")

```

also, add the following line at the beginning of method on_sync_source():

```

input_file = input_file.replace("%20", " ")

```

3. finally, in the evince shell script, make sure that you invoke your editor quoting the file name.

Hope this helps!
Marciano.

---

### Post by mjacek on 2012-10-04
In my installation emacs tried to treat uri of the file literally - it visited a file with name /home/mjacek/file:/home/mjacek/latex/mypaper.tex, which was nonexistent...


After trying strange things, I hacked the evince_backward_search script with a line to strip the "file:" uri prefix:


        cmd = re.sub("%l",str(source_link[0]), cmd)
##mjacek added next line
 cmd = re.sub("file:","",cmd)
## 
        print cmd
 
... and now it works OK

I also needed to use patches from [http://ubuntuforums.org/showpost.php?p=10771326&postcount=5](http://ubuntuforums.org/showpost.php?p=10771326&postcount=5) , otherwise I got dbus error.

PS. When editing Python code do remember that indentation counts - align the new line exactly with old ones, not the other way round :-)

---

### Post by deven2u on 2012-10-18
Hello Ben and all the other guys who contributed,

Great work! I am in the proof reading stage of my thesis (and can't use dvi format because of tikz and pgfplots). This app has till date, at least saved me 50% of the efforts.

Cheers,
Devendra

---

### Post by macsa on 2012-12-03
Hello all, 

I got that working for vim on Ubuntu 12.10. The only problem is that if I do ctrl-click in evince to jump to vim, vim starts two windows. One is working and I can jump through the document via forward and backward search. The second window is just a replica of the first one with the same document and I have to manuelly close that one. Can you help me? Maybe there is a newer version of the script for ubuntu 12.10.

Thank you!

---

### Post by quasus on 2013-03-13
> **macsa said:**
> Hello all, 

I got that working for vim on Ubuntu 12.10. The only problem is that if I  do ctrl-click in evince to jump to vim, vim starts two windows. One is  working and I can jump through the document via forward and backward  search. The second window is just a replica of the first one with the  same document and I have to manuelly close that one. Can you help me?  Maybe there is a newer version of the script for ubuntu 12.10.

Thank you!

I've had a similar problem: as I have a .tex file open in gvim,  evince opens another instance of the same file in a tab prefixed with 'file://' (I use '-remote-tab-silent'). I've changed
        cmd = re.sub("%f",input_file[7:],self.editor)
to
        cmd = re.sub("%f",input_file[7:],self.editor)
in evince_backward_search (thus stripping unwanted prefix), and now it works.

Many thanks to the author and contributors! The scripts are great.

---

### Post by rehanog on 2013-03-27
Thanks a lot for a great tool.

How about putting it on github?

Rehan

---

### Post by a.fiodorov on 2013-08-13
woth pointing out that the right path for those who use vundle (instead of vim-latexsuite package) is
~/.vim/bundle/vim-latex/after/ftplugin/tex.vim

---

### Post by whophil on 2014-06-03
Bringing this back from the dead -- seems like this issue also affects filenames/paths that have other special characters in them. For example, forward and backward search don't work for files that have "[" or "]" characters in them on my Ubuntu system.

It seems like some additional escaping might be needed for other special characters.

---

### Post by gonghan on 2014-10-25
Has anyone tried this on 14.04? I did not succeed. Any ideas please?


I have sorted the issue. In 14.04, the dbus interface has been changed. The solution is found at #5.

---

