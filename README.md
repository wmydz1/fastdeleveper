# fastdeveleper
# 这是Android开发常用库的集合
- 用于快速开发APP 

## Gson
Student.java
```
package com.logoocc.json_java;

/**
 * Created by samchen on 8/20/15.
 */
public class Student {

    private String name;
    private int id;
    private String phone;
    private int age;

    public String getName() {
        return name;
    }

    public void setName(String name) {
        this.name = name;
    }

    public int getId() {
        return id;
    }

    public void setId(int id) {
        this.id = id;
    }

    public String getPhone() {
        return phone;
    }

    public void setPhone(String phone) {
        this.phone = phone;
    }

    public int getAge() {
        return age;
    }

    public void setAge(int age) {
        this.age = age;
    }
}


```
Main.java 部分代码
```

    Student s = new Student();
        s.setAge(100);
        s.setName("samchen");
        s.setId(1);
        s.setPhone("168888");
   
        Gson gson = new Gson();
        // Object -> Json
        String jsonStr = gson.toJson(s);
         // List -> Json
         List<Student> students = new ArrayList<Student>();
         String jsonarray = gson.toJson(students);
         
         // Json -> Object
        Student student = gson.fromJson(jsonStr, Student.class);
        // Json -> List
          List<Student> ss =gson.fromJson(jsonarray,new TypeToken<List<Student>>(){}.getType());
```
___

## 泛型的使用
```
public class Result<T> {
    private int status;
    private String message;
    private T data;

    public int getStatus() {
        return status;
    }

    public void setStatus(int status) {
        this.status = status;
    }

    public String getMessage() {
        return message;
    }

    public void setMessage(String message) {
        this.message = message;
    }

    public T getData() {
        return data;
    }

    public void setData(T data) {
        this.data = data;
    }

}


```

```
    private void createBean() {
        Result<Student> result = new Result<Student>();
        result.setStatus(1);
        result.setMessage("登陆成功");
        Student s = new Student();
        s.setAge(100);
        s.setName("samchen");
        s.setId(1);
        result.setData(s);
        Gson gson = new Gson();
        // T -> Json
        Log.i("sss", gson.toJson(result));
      //  Json ->T
         Result rt = gson.fromJson(str, new TypeToken<Result<Student>>() {
        }.getType());
        Log.i("rr",rt.getMessage());
    }

```
