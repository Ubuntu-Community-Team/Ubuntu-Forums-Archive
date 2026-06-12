---
title: "accessing shared smb windows drive in ruby/python scripts"
date: 2009-02-16
forum: General Help
---

### Post by sa125 on 2009-02-16
I have a shared windows drive on my network that I can access in nautilus using smb://servername/sharedfolder or smb://<ip-address>/sharedfolder.

I need to be able to access it via ruby and python scripting from my ubuntu machine (8.10), but I can't figure out how. I tried the obvious way (same address as nautilus), but wasn't successful.

To play around, I tried printing the content of that folder with both:

1. with ruby```

Dir.entries("smb://servername/sharedfolder").each do |file|
  puts file
end
```
2. with python```

for file in os.listdir("smb://servername/sharedfolder")
    print file
```
Both give me "no file or directory" error on that path.

I'd really appreciate help on this - thanks.

---

