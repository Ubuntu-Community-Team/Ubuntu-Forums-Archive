---
title: "Method required to add semi colon to end of names in large list"
date: 2009-01-27
forum: General Help
---

### Post by Rytron on 2009-01-27
Hi. I have a large list of names in a text file. Is there a quick method to add a semi colon i.e. ; 
to the end of each name?

---

### Post by sdennie on 2009-01-27
Are the filenames one per line?  If so, try:

```

sed -e "s/$/\;/" name_of_file

```

If that looks like the correct output, you can apply the change with:

```

sed -i -e "s/$/\;/" name_of_file

```

---

### Post by Rytron on 2009-01-27
Thank you very much sdennie. Pure genius.
:mrgreen:

---

