## os.fork
> 语法帮助信息 

```
>>> os.fork?
fork() -> pid
Fork a child process.
Return 0 to child process and PID of child to parent process.
译:
return pid
Fork一个子进程.
如果pid是0表示是父进程对应的子进程.
```

> fork示例  

```
import os
    
print os.getpid()
print 'before fork.'
pid = os.fork()
print 'after fork.'
if pid == 0:
    print 'child pid %s' % os.getpid()
    print 'father pid %s in child.' %  os.getppid()
else:
    print 'father pid %s' % os.getpid()
```
> 执行输出结果  

```
1749
before fork.
after fork.
father pid 1749
after fork.
child pid 1750
father pid 1749 in child.
```

> 结论  

```
1. 父进程、子进程是异步执行的.
2. 父进程的pid是子进程的ppid.
3. 子进程从父进程中clone一份同样的地址空间 两者独立 互不影响
```
