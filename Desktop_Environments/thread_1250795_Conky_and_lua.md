---
title: "Conky and lua"
date: 2009-08-26
forum: Desktop Environments
---

### Post by slakkie on 2009-08-26
```

do
    printf = function(s,...)
        return (s:format(...))
    end

    function conky_test_multiline(line1, line2)
        return printf("$alignr %s\n%s", line1, line2)
    end

end

```

Expected output:
```

                    line1
line2

```

Get
```

                    line1
                    line2

```

The same happens when I use alignc:
```

    function conky_test_multiline(line1, line2)
        return printf("$alignr %s\n%s", line1, line2)
    end

```

How can I get one lua function to print two lines correctly when using align[cr]?

---

