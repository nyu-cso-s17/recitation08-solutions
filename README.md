Recitation 8 - Solutions
-----

The answers to the questions are:

1) 'x' starts in register $rdi and gets returned in $rax in function addone2. It is in memory location 0x7fffffffdfe8 in addone (The address value in addone may be slightly different depending on the student's machine but I have asked them to send screenshots of their work. As long as the address resembles the value mentioned here that is good enough for full credit)

2) Instructions corresponding to line 12 are:

```
12      (*x)++;
=> 0x0000000000400562 <addone+0>:   48 8b 07    mov    (%rdi),%rax
   0x0000000000400565 <addone+3>:   48 83 c0 01 add    $0x1,%rax
   0x0000000000400569 <addone+7>:   48 89 07    mov    %rax,(%rdi)
```

3) The instruction that causes the segmentation fault is:

```
=> 0x0000000000400562 <addone+0>:   48 8b 07    mov    (%rdi),%rax
```

The variable x holds the value 2, and x is a long *. This will clearly led to a segmentation fault when x is dereferenced. The specific instruction that does this is the one marked with the arrow: mov (%rdi),%rax. Trying to take the value at the address given by register %rdi, or trying to dereference x, causes the segmentation fault (line 27 of the source code to see the function call).