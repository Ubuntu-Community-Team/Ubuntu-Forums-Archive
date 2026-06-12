---
title: "Reading images in octave!"
date: 2010-04-08
forum: Education &amp; Science
---

### Post by srikar on 2010-04-08
To read an image we use ```
img=imread("image.jpg");
```

suppose there are 100's of images in a folder...how to read them as above. I mean we cant write 100 statements with different file names...?

---

### Post by normandin on 2010-04-16
You might do well to try something like:
```

x = dir ("*.jpg");   # get struct of info on .jpg's in directory
for ii = 1:length (x)   # loop over jpg files
  img = imread (x(ii).name);   # read image file
  ## MANIPULATE IMAGE HERE
end

```

This assumes that you can/want to handle the images individually.  You'll need to modify the loop if multiple images need to be worked on at once.

---

### Post by carandraug on 2010-04-18
> **srikar said:**
> To read an image we use ```
img=imread("image.jpg");
```

suppose there are 100's of images in a folder...how to read them as above. I mean we cant write 100 statements with different file names...?

If you want to have all 100 images loaded at the same time (you may want to do operations with them) you can use a cell array. For example:

```

for i = 1:length(image_filepaths)
  img{i} = imread(image_filepaths{i});
endfor

```
alternatively, if you want to have the filepath together with the image

```

for i = 1:length(image_filepaths)
  img(i).filepath = image_filepaths{i};
  img(i).data     = imread(image_filepaths{i});
endfor

```

---

