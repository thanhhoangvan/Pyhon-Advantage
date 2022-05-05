<h1 align='center'>Python Decorator</h1>

# Hàm trong Python
Hàm là một đối trượng trong Python thực hiện một chức năng nào đó mà chúng ta lập trình.\
Ví dụ:
```python
>>> def SUM(a, b):
        return a+b

>>> print(SUM(2, 3))
5
>>> TONG = SUM
>>> TONG(2, 3)
5
```
Ta thấy khi gọi `TONG` và `SUM` đều cho ra kết quả giống nhau khi đối số truyền vào là như nhau. Vậy hai đối tượng `TONG` và `SUM` đều là hai đối tượng hàm và đều trỏ tới cùng một đối tượng.

# Tham số của hàm là một hàm khác
Một hàm có tham số của hàm là một hàm khác thì được gọi là **hàm bậc cao(High-order functions)** \
Ví dụ:
```python
>>> def inc(x):
        return x+1
>>> def dec(x):
        return x-1
>>> def operate(func, x):
        result = func(x)
        return result
>>> operate(inc, 4)
5
>>> opoerate(dec, 4)
3
```

# Hàm trả về một hàm khác
Một hàm có thể trả về một kết quả là một đối tượng hàm.\
Ví dụ:
```python
>>> def make_func():
        def sum(x, y):
            return x+y
        return sum
>>> tong = make_func()
>>> tong(3, 5)
8
```

# Decotrator
Decorator nhận vào một hàm, cho phép chạy môt số đoạn code trước hoặc sau khi vào hàm đó mà không thay đổi kết quả.\
Ví dụ:
```python
>>> def show():
        return 'Hello'

>>> def make_logs(func):
        def inner():
            print('Decorator')
            func()
        return inner

>>> make_logs(show)
Decorator
Hello
```

Cú pháp đơn gản hơn:
```python
@ make_lgos
def show():
    return 'Hello'
```

Với hàm có tham số
```python
def make_decor(func):
    def inner(a, b):
        print("SUM:")
        func(a,b)
    return inner

@make_decor
def sum(a, b)
    return a+b
```

# Chú ý:
- Một hàm có thể áp dụng nhiều decorator
- Một decorator có thể được áp dụng lên nhiều hàm