---
title: "Getting an Amarok script to run again (songmeanings.net)"
date: 2009-01-03
forum: General Help
---

### Post by Cclips on 2009-01-03
So for some reason or another the songmeanings.net lyrics script doesn't want to function properly. It gives me a message saying that the server can't be reached, though you can get to the site via a browser with no problems. It used to work without a hitch, but somewhere along the line it stopped (don't remember when). Anyways the script is here 

```
#!/usr/bin/env python
import urllib, re
from sys import stdin
from os import system
from xml.dom import getDOMImplementation
try:
 dom = getDOMImplementation()
except ImportError:
 system("kdialog --sorry 'Sorry, this script requires the xml.dom.getDOMImplementation function.'")
 exit()
def __splitartistsong(data):
 f = data.split(' - ')
 if len(f) > 2: #We will assume that there is no artist with " - " in the name.
  f = [' - '.join(f[:-1]), f[-1]]
 return f #f[0] = songname, f[1] = artist
def song(artist, songname, newurl=None):
 if artist == False:
  data = songname
  page = newurl
 else:
  page = "http://www.songmeanings.net/query.php?action=title&query=" + urllib.quote_plus(songname)
  try:
   data = urllib.urlopen(page).read()
  except IOError:
   system('dcop amarok playlist popupMessage "Network input/output error when retrieving lyrics.  Try again later."')
   return
 if data.find('<title>SongMeanings | lyrics') != -1: #ok, we've got a lyrics page
  tmp = data[data.find('<title>SongMeanings | lyrics | ')+31:data.find('</title>')].split(' - ')
  if len(tmp) > 2:
   songname = ' - '.join(tmp[1:])
   tmp = tmp[1]
  else:
   songname, tmp = tmp[1], tmp[0]
  if artist != False and tmp.lower() != artist.lower(): return "matches", page, ()
  data = data[data.find('<td width="100%" style="text-align:left;">')+5:]
  data = data[data.find('<td width="100%" style="text-align:left;">')+42:]
  data = data[:data.find('</td>')]
  data = data.replace('\n', '').replace('\r', '').replace('<br />', '\n')
  while data[:1] == ' ' or data[:1] == '\n':
   data = data[1:]
  while data[-1] == ' ' or data[-1] == '\n':
   data = data[:-1]
  if artist == False: artist = tmp
  return "lyrics", page, artist, songname, data
 elif data.find('<title>SongMeanings | search results for') != -1: # search results page
  matches = re.findall('<a href="query.php\?action=go&lid=(\d+)" title="(.+?)">.+?</a>', data, re.M)
  for i in matches:
   f = __splitartistsong(i[1])
   if f[0].lower() == songname.lower() and f[1].lower() == artist.lower(): #ohay, we've got a match
    try:
     url = "http://www.songmeanings.net/query.php?action=go&lid=" + i[0]
     return song(False, urllib.urlopen(url).read(), url)
    except IOError:
     system('dcop amarok playlist popupMessage "Network input/output error when retrieving lyrics at %s.  Try again later."' % i[0])
     return
   else:
     continue
  return "matches", page, matches # return the whole list if we haven't got any exact matches
 elif data.find('<title>SongMeanings | error') != -1: # no results
  return "matches", page, ()
def amarok_xml_result(input=None, url=None, arg1=None, arg2=None, arg3=None):
 if input == None: return
 if type(input) == tuple:
  try:
   arg3 = input[4]
  except IndexError:
   pass
  try:
   arg2 = input[3]
  except IndexError:
   pass
  try:
   arg1 = input[2]
  except IndexError:
   pass
  url = input[1]
  input = input[0]
 if input == "matches": #suggestions page
  doc = dom.createDocument('', 'suggestions', '')
  for i in arg1:
   node = doc.documentElement.appendChild(doc.createElement('suggestion'))
   song, artist = __splitartistsong(i[1])
   node.setAttribute('artist', artist)
   node.setAttribute('title', song)
   node.setAttribute('url', "http://www.songmeanings.net/lyric.php?lid=%s" % i[0])
 elif input == "lyrics": #exact match
  doc = dom.createDocument('', 'lyrics', '')
  doc.documentElement.setAttribute('title', arg2)
  doc.documentElement.setAttribute('artist', arg1)
  doc.documentElement.appendChild(doc.createTextNode(arg3))
 else:
  system('kdialog --sorry "%s"' % str(input))
  return
 doc.documentElement.setAttribute('page_url', url)
 return doc.toxml().replace('"', '\\"')
while True:
 command = stdin.readline().rstrip()
 if not command: break
 command2 = command.split(' ')
 if command2[0] == 'configure':
  system('kdialog --sorry "This script does not have configuration options."')
 elif command2[0] == 'fetchLyrics':
  res = amarok_xml_result(song(urllib.unquote(command2[1]), urllib.unquote(command2[2])))
  system('dcop amarok contextbrowser showLyrics "%s"' % res)
 elif command2[0] == 'fetchLyricsByUrl':
  try:
   res = amarok_xml_result(song(False, urllib.urlopen(command2[1]).read(), command2[1]))
  except IOError:
   system('dcop amarok playlist popupMessage "Network input/output error when retrieving lyrics.  Try again later."')
  else:
   system('dcop amarok contextbrowser showLyrics "%s"' % res)
```

If you see anything obvious. My first thought was that songmeanings.net changed something on their end. But the author also states that it requires python 2.4 and the "python re module" and "python xml module".

I tried installing python 2.4 and the xml module, or at least what I thought was one, to no avail. I couldn't find an obvious python re module to install however.

---

### Post by Cclips on 2009-01-04
bump

---

