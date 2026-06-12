---
title: "Help debugging thumbnailer stl-thumb"
date: 2020-06-25
forum: Desktop Environments
---

### Post by treii28 on 2020-06-25
[COLOR=#242729][FONT=Arial]I recently installed 'stl-thumb' as a thumbnailer plugin to the file managers, but I notice that it isn't converting all files with the .stl extension. Upon closer inspection using the shell 'file --mime, the files that are "working" are binary encoded STL files but the ones that are not are ascii encoded STL files. Testing the script from the command line, however, shows that it works on both types of files.[/FONT][/COLOR]
[COLOR=#242729][FONT=Arial]Building a wrapper around the stl-thumb binary script archive so I can drop a log, I can see that it is not even attempting to do anything with the ascii encoded files. So I'm assuming it's something at the OS/file-manager level seeing those files as different.

The thumbnailer definition file is:
[/FONT][/COLOR][INDENT][FONT=courier new][Thumbnailer Entry]
TryExec=stlthumbnailer
Exec=stlthumbnailer -f png -s %s %i %o 
MimeType=model/stl;model/x.stl-ascii;model/x.stl-binary;application/sla;
[/FONT][/INDENT]
[COLOR=#242729][FONT=Arial]
When I pull up properties for both types of files in the file-manager, the mime types listed for both show up as:[/FONT][/COLOR]
[COLOR=#242729][FONT=Arial]
[/FONT][/COLOR][INDENT][COLOR=#242729][FONT=Arial][FONT=courier new]Unknown (model/x.stl-binary)[/FONT][/FONT][/COLOR][FONT=courier new]
[/FONT][/INDENT]
[COLOR=#242729][FONT=Arial]
Checking from the command line with file however shows:
[/FONT][/COLOR][INDENT][FONT=courier new]$ file --mime *.stl
binary_test.stl:   application/octet-stream; charset=binary
ascii_test.stl: text/plain; charset=us-ascii

$ file -b --mime *.stl
application/octet-stream; charset=binary
text/plain; charset=us-ascii
[/FONT][/INDENT]
[COLOR=#242729][FONT=Arial]
Again, the thumbnailer script runs on teh binary encoded file, but doesn't appear to be run at all on the ascii encoded one. So I'm assuming it has either something to do with the mime types or the difference in content. Running the script manually on the ascii encoded file does work fine.[/FONT][/COLOR]
[COLOR=#242729][FONT=Arial]I'm not sure what to tweak to get it working properly.[/FONT][/COLOR]

---

