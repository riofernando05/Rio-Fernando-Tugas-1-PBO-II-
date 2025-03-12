## Rio-Fernando-Tugas-1-PBO-II-

1. Prototype dalam design pattern adalah pola desain yang digunakan untuk membuat objek baru dengan menyalin objek yang sudah ada daripada membuat objek baru dari awal. Pola ini termasuk _creational design pattern_ karena berfokus dalam pembuatan objek.
   
2. Design pattern prototype dapat digunakan dalam beberapa situasi berikut:
   - Membuat objek serupa dalam jumlah banyak
     Jika aplikasi yang sedang dikembangkan membutuhkan banyak objek yang hampir serupa (misal beberapa entitas atau produk yang sebagian besar atributnya sama). Dalam situasi ini prototype digunakan untuk mengkloning objek yang sudah ada dan hanya memodifikasi atribut yang dibutuhkan. Contohnya dalam sistem pengelolaan produk, biasanya memiliki beberapa produk yang hampir identik, kecuali untuk beberapa atribut, seperti nama atau harga.
     
   - Saat objek memiliki banyak variasi dan pengguna harus memodifikasi atribut
     Dalam beberapa kasus, terdapat objek yang memiliki banyak variasi, tetapi semua variasi itu memiliki atribut yang sebagian besar sama. Disini prototype digunakan untuk mengkloning objek dan mengubah bagian-bagian tertentu yang dibutuhkan. Contohnya di dalam video game, karakter dengan atribut yang hampir sama (level, atribut, keahlian) dapat dibuat dengan mengkloning karakter prototipe, kemudian memodifikasi nama atau atribut lainnya sesuai kebutuhan.
     
3.   Kelebihan design pattern prototype:
   - Lebih efisien dalam membuat objek: Prototype memungkinkan mengkloning objek yang sudah ada daripada membuatnya dari nol. Ini sangat menghemat waktu dan sumber daya, terutama jika objek yang dibuat terlalu kompleks.
   - Lebih fleksibel dalam membuat objek: Objek baru dapat dibuat dengan mengkloning objek yang sudah ada kemudian memodifikasi beberapa atributnya sesuai kebutuhan.
     
     Kekurangan:
   - Kesulitan jika objek terlalu kompleks: Jika objek yang akan dikloning sangat kompleks, proses kloning bisa menjadi sangat sulit dan membingungkan. Memastikan semuanya terkloning dengan benar bisa menjadi tantangan besar.
     
   - Membuat kode menjadi lebih rumit: Meskipun prototype bisa membantu dalam beberapa kasus, terkadang menambahkan pola ini justru bisa membuat kode menjadi lebih rumit, karena harus menambahkan logika untuk mengkloning objek dengan benar. Ini bisa membuat pengelolaan kode sedikit lebih susah.
  
4. Contoh coding Java:
```java
public interface Prototype {
    Prototype clone();
}
public class ConcretePrototype implements Prototype {
    private String name;
    private int age;

    // Constructor
    public ConcretePrototype(String name, int age) {
        this.name = name;
        this.age = age;
    }

    // Getter dan Setter
    public String getName() {
        return name;
    }

    public void setName(String name) {
        this.name = name;
    }

    public int getAge() {
        return age;
    }

    public void setAge(int age) {
        this.age = age;
    }

    // Implementasi metode clone() untuk menduplikasi objek ini
    @Override
    public Prototype clone() {
        // Menggunakan constructor untuk membuat objek baru dengan data yang sama
        return new ConcretePrototype(this.name, this.age);
    }

    @Override
    public String toString() {
        return "ConcretePrototype { " +
                "name='" + name + '\'' +
                ", age=" + age +
                " }";
    }
}
public class Client {
    public static void main(String[] args) {
        // Membuat objek asli
        ConcretePrototype prototype1 = new ConcretePrototype("Rio", 20);

        // Menduplikasi objek prototype1
        ConcretePrototype prototype2 = (ConcretePrototype) prototype1.clone();
        
        // Mengubah data pada prototype2 agar berbeda dengan prototype1
        prototype2.setName("Reo");
        prototype2.setAge(21);

        // Menampilkan hasil
        System.out.println("Original: " + prototype1);
        System.out.println("Clone: " + prototype2);
    }
}
