---
title: "Removing  &quot;;1&quot;   from file extension"
date: 2009-05-13
forum: General Help
---

### Post by kulkarniniraj on 2009-05-13
Hello
   I am not sure if I am posting this question in right forum, actually it's been long time since I used to write shell scripts so i forgot linux commands.

 Actually I just downloaded a game setup (which runs on windows).I want to run it through wine on ubuntu.

The problem is that every file in that setup has an extra symbol ';1' after filename eg AUTORUN.exe;1  setup.exe;1 etc. I dont know if windows recognises it but wine is not. 

    So I want to write a shell script which would remove these 2 extra characters from each filename, recursively from subfolders also.

  Can anybody help me please.

---

### Post by kaibob on 2009-05-13
The following will do what you want:

```
find /directory/name -name '*;1' -type f -exec rename -n 's/;1$//' '{}' ';'
```

The -n option does a dry run and reports proposed changes. Substitute -v for -n to actually rename the files. Also, you need to change /directory/name to the name of the target directory.

---

### Post by ghostdog74 on 2009-05-13
```

for file in *;1
do
 mv "$file" "${file/;1/}"
done

```

---

### Post by kulkarniniraj on 2009-05-13
Thanks that worked

---

