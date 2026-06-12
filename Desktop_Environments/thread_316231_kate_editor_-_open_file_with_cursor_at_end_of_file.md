---
title: "kate editor - open file with cursor at end of file"
date: 2006-12-10
forum: Desktop Environments
---

### Post by RHTopics on 2006-12-10
Does anyone know the command line syntax to have the editor kate open an existing text file and position the cursor at the end of the file?

Using the following command;

```
kate --line 621 /home/user/sample.txt 
```

will start kate and open the file at line 621.

Yet, the file I want to edit is a manual entry log file and want it opened with the cursor positioned at the end of the file to add a new entry.

---

### Post by RHTopics on 2006-12-10
Using the 'wc -l' word count command, I found a solution to my question.

example:

```
kate  --line $(wc -l /home/user/sample.txt)
```

I still would be interested in knowing if kate itself has command line option to do this instead.

---

