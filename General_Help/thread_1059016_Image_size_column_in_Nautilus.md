---
title: "Image size column in Nautilus"
date: 2009-02-03
forum: General Help
---

### Post by Major_Kong on 2009-02-03
Just wondering, is there a script/plugin for nautilus in order to add image size column ?

---

### Post by Major_Kong on 2009-02-04
Copied some code from a python script and created what i wanted:

```
#!/usr/bin/python

# this script can installed to the user account by running the following commands:

# sudo apt-get install python-nautilus
# mkdir ~/.nautilus/python-extensions
# cp imgsc.py ~/.nautilus/python-extensions
# chmod a+x ~/.nautilus/python-extensions/imgsc.py


import nautilus
import urllib
# for extracting the image size
import Image

class ColumnExtension(nautilus.ColumnProvider, nautilus.InfoProvider):
	def __init__(self):
		pass

	def get_columns(self):
		return (nautilus.Column("NautilusPython::img_size_column",
					"img_size",
					"Image Size",
					"Image Size"),
			nautilus.Column("NautilusPython::img_width_column",
					"img_width",
					"Width",
					"Image Width"),
			nautilus.Column("NautilusPython::img_height_column",
					"img_height",
					"Height",
					"Image height")
			)

	def update_file_info(self, file):
		if file.get_uri_scheme() != 'file':
			return

		if file.is_mime_type('image/jpeg') or file.is_mime_type('image/png') or file.is_mime_type('image/gif'):
			filename = urllib.unquote(file.get_uri()[7:])
			im = Image.open(filename)		
			file.add_string_attribute('img_size', str(im.size[0]) + ' x ' + str(im.size[1]) )
			file.add_string_attribute('img_width', str(im.size[0]))
			file.add_string_attribute('img_height', str(im.size[1]))
		else:
			file.add_string_attribute('img_size', '')
			file.add_string_attribute('img_width', '')
			file.add_string_attribute('img_height', '')


		self.get_columns()
```

Until native support for a image size column is added to nautilus, i  guess this will do.

---

