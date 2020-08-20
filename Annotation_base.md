# Java ע�⣨Annotation��

Java ע�⣨Annotation���ֳ� Java ��ע���� JDK5.0 �����һ��ע�ͻ��ơ�
Java �����е��ࡢ�����������������Ͱ��ȶ����Ա���ע���� Javadoc ��ͬ��Java ��ע����ͨ�������ȡ��ע���ݡ��ڱ������������ļ�ʱ����ע���Ա�Ƕ�뵽�ֽ����С�Java ��������Ա�����ע���ݣ�������ʱ���Ի�ȡ����ע���� �� ��Ȼ��Ҳ֧���Զ��� Java ��ע��

���Ϻܶ���� Java Annotation �����£��������ۻ����ҡ�Java Annotation �����ܼ򵥵ģ����˵����û˵�����Ū�Ŀ����˸����Ժ���

�Ұ����Լ���˼·���� Annotation ������������� Annotation �Ĺؼ�������� Annotation ���﷨���÷�������Щ���ݣ��Ҷ���������ϸ˵������� Annotation ���﷨���÷�֮���ٿ� Annotation �Ŀ��ͼ�������и������ᡣ�ϻ���˵��ô�࣬���濪ʼ�� Annotation ����˵�����������������д��ڴ������ĵط���ϣ������ָ����

## ���õ�ע��
Java ������һ��ע�⣬���� 7 ����3 ���� java.lang �У�ʣ�� 4 ���� java.lang.annotation �С�

�����ڴ����ע����

@Override - ���÷����Ƿ�����д��������������丸�࣬���������õĽӿ��в�û�и÷���ʱ���ᱨ�������
@Deprecated - ��ǹ�ʱ���������ʹ�ø÷������ᱨ���뾯�档
@SuppressWarnings - ָʾ������ȥ����ע���������ľ��档
����������ע���ע��(����˵ Ԫע��)��:

@Retention - ��ʶ���ע����ô���棬��ֻ�ڴ����У����Ǳ���class�ļ��У�������������ʱ����ͨ��������ʡ�
@Documented - �����Щע���Ƿ�������û��ĵ��С�
@Target - ������ע��Ӧ�������� Java ��Ա��
@Inherited - ������ע���Ǽ̳����ĸ�ע����(Ĭ�� ע�Ⲣû�м̳����κ�����)
�� Java 7 ��ʼ����������� 3 ��ע��:

@SafeVarargs - Java 7 ��ʼ֧�֣������κ�ʹ�ò���Ϊ���ͱ����ķ������캯�����ò����ľ��档
@FunctionalInterface - Java 8 ��ʼ֧�֣���ʶһ��������������ʽ�ӿڡ�
@Repeatable - Java 8 ��ʼ֧�֣���ʶĳע�������ͬһ��������ʹ�ö�Ρ�
### 1��Annotation �ܹ�


���У����ǿ��Կ�����

(01) 1 �� Annotation �� 1 �� RetentionPolicy ������

�������Ϊ��ÿ1��Annotation���󣬶�����Ψһ��RetentionPolicy���ԡ�
(02) 1 �� Annotation �� 1~n �� ElementType ������

�������Ϊ������ÿ 1 �� Annotation ���󣬿��������ɸ� ElementType ���ԡ�

(03) Annotation �����ʵ���࣬������Deprecated, Documented, Inherited, Override �ȵȡ�

Annotation ��ÿһ��ʵ���࣬�� "�� 1 �� RetentionPolicy ����" ���� " �� 1~n �� ElementType ����"��

���棬���Ƚ��ܿ��ͼ������(����ͼ)���� Annotation, RetentionPolicy, ElementType��Ȼ���ھ� Annotation ��ʵ������о���˵����



### 2��Annotation ��ɲ���
java Annotation ������У��� 3 ���ǳ���Ҫ�������ࡣ���Ƿֱ��ǣ�

Annotation.java
package java.lang.annotation;
public interface Annotation {

    boolean equals(Object obj);

    int hashCode();

    String toString();

    Class<? extends Annotation> annotationType();
}
ElementType.java
package java.lang.annotation;

public enum ElementType {
    TYPE,               /* �ࡢ�ӿڣ�����ע�����ͣ���ö������  */

    FIELD,              /* �ֶ�����������ö�ٳ�����  */

    METHOD,             /* ��������  */

    PARAMETER,          /* ��������  */

    CONSTRUCTOR,        /* ���췽������  */

    LOCAL_VARIABLE,     /* �ֲ���������  */

    ANNOTATION_TYPE,    /* ע����������  */

    PACKAGE             /* ������  */
}
RetentionPolicy.java
package java.lang.annotation;
public enum RetentionPolicy {
    SOURCE,            /* Annotation��Ϣ�������ڱ����������ڼ䣬������������֮���û�и�Annotation��Ϣ��  */

    CLASS,             /* ��������Annotation�洢�����Ӧ��.class�ļ��С�Ĭ����Ϊ  */

    RUNTIME            /* ��������Annotation�洢��class�ļ��У����ҿ���JVM���� */
}
˵����

(01) Annotation ���Ǹ��ӿڡ�

"ÿ 1 �� Annotation" ���� "1 �� RetentionPolicy" ������������ "1��n �� ElementType" ����������ͨ�׵����Ϊ��ÿ 1 �� Annotation ���󣬶�����Ψһ�� RetentionPolicy ���ԣ����� ElementType ���ԣ����� 1~n ����

(02) ElementType �� Enum ö�����ͣ�������ָ�� Annotation �����͡�

"ÿ 1 �� Annotation" ���� "1��n �� ElementType" �������� Annotation ��ĳ�� ElementType ����ʱ������ζ�ţ�Annotation����ĳ����;�����磬��һ�� Annotation ������ METHOD ���ͣ���� Annotation ֻ���������η�����

(03) RetentionPolicy �� Enum ö�����ͣ�������ָ�� Annotation �Ĳ��ԡ�ͨ�׵�˵�����ǲ�ͬ RetentionPolicy ���͵� Annotation ��������ͬ��

"ÿ 1 �� Annotation" ���� "1 �� RetentionPolicy" ������

a) �� Annotation ������Ϊ SOURCE������ζ�ţ�Annotation �������ڱ����������ڼ䣬������������֮�󣬸� Annotation ��û���ˡ� ���磬" @Override" ��־����һ�� Annotation����������һ��������ʱ�򣬾���ζ�Ÿ÷������Ǹ���ķ����������ڱ����ڼ������﷨��飡�������������"@Override" ��û���κ������ˡ�
b) �� Annotation ������Ϊ CLASS������ζ�ţ��������� Annotation �洢�����Ӧ�� .class �ļ��У����� Annotation ��Ĭ����Ϊ��
c) �� Annotation ������Ϊ RUNTIME������ζ�ţ��������� Annotation �洢�� class �ļ��У����ҿ���JVM���롣
��ʱ��ֻ��Ҫ��ס"ÿ 1 �� Annotation" ���� "1 �� RetentionPolicy" ������������ "1��n �� ElementType" ������ѧ����������֮���ٻ�ͷ����Щ���ݣ����������⡣

### 3��java �Դ��� Annotation
���������� 3 ���������֮�����ǽ��������Խ��� Annotation ʵ������﷨�����ˡ�

1��Annotation ͨ�ö���
@Documented
@Target(ElementType.TYPE)
@Retention(RetentionPolicy.RUNTIME)
public @interface MyAnnotation1 {
}
˵����

����������Ƕ���һ�� Annotation������������ MyAnnotation1�������� MyAnnotation1 ֮�����ǿ����ڴ�����ͨ�� "@MyAnnotation1" ��ʹ������ �����ģ�@Documented, @Target, @Retention, @interface ���������� MyAnnotation1 �ġ�����ֱ�˵˵���ǵĺ��壺

(01) @interface

ʹ�� @interface ����ע��ʱ����ζ����ʵ���� java.lang.annotation.Annotation �ӿڣ�����ע�����һ��Annotation��

���� Annotation ʱ��@interface �Ǳ���ġ�
ע�⣺��������ͨ���� implemented ʵ�ֽӿڵķ�����ͬ��Annotation �ӿڵ�ʵ��ϸ�ڶ��ɱ�������ɡ�ͨ�� @interface ����ע��󣬸�ע�ⲻ�ܼ̳�������ע���ӿڡ�

(02) @Documented

��ͷ����� Annotation ��ȱʡ������ǲ������� javadoc �еġ����ʹ�� @Documented ���θ� Annotation�����ʾ�����Գ����� javadoc �С�

���� Annotation ʱ��@Documented ���п��ޣ���û�ж��壬�� Annotation ��������� javadoc �С�

(03) @Target(ElementType.TYPE)

ǰ������˵����ElementType �� Annotation ���������ԡ��� @Target �����ã�������ָ�� Annotation ���������ԡ�

@Target(ElementType.TYPE) ����˼����ָ���� Annotation �������� ElementType.TYPE�������ζ�ţ�MyAnnotation1 ��������"�ࡢ�ӿڣ�����ע�����ͣ���ö������"��ע�⡣

���� Annotation ʱ��@Target ���п��ޡ����� @Target����� Annotation ֻ����������ָ���ĵط�����û�� @Target����� Annotation ���������κεط���

(04) @Retention(RetentionPolicy.RUNTIME)

ǰ������˵����RetentionPolicy �� Annotation �Ĳ������ԣ��� @Retention �����ã�����ָ�� Annotation �Ĳ������ԡ�

@Retention(RetentionPolicy.RUNTIME) ����˼����ָ���� Annotation �Ĳ����� RetentionPolicy.RUNTIME�������ζ�ţ��������Ὣ�� Annotation ��Ϣ������ .class �ļ��У������ܱ��������ȡ��

���� Annotation ʱ��@Retention ���п��ޡ���û�� @Retention����Ĭ���� RetentionPolicy.CLASS��

2��java�Դ���Annotation
ͨ�������ʾ������������⣺@interface �������� Annotation��@Documented ������ʾ�� Annotation �Ƿ������� javadoc �У� @Target ����ָ�� Annotation �����ͣ�@Retention ����ָ�� Annotation �Ĳ��ԡ�

�����һ��֮�����Ǿͺ�������� java ���Դ��� Annotation ��ʵ���࣬�� Annotation �ܹ�ͼ���Ұ�ߡ�����ͼ��



# java ���õ� Annotation��

@Deprecated  -- @Deprecated ����ע���ݣ����ٱ�����ʹ�á�
@Override    -- @Override ֻ�ܱ�ע��������ʾ�÷������Ǹ����еķ�����
@Documented  -- @Documented ����ע���ݣ����Գ�����javadoc�С�
@Inherited   -- @Inheritedֻ�ܱ�������ע��Annotation���͡���������ע��Annotation���м̳��ԡ�
@Retention   -- @Retentionֻ�ܱ�������ע��Annotation���͡���������������ָ��Annotation��RetentionPolicy���ԡ�
@Target      -- @Targetֻ�ܱ�������ע��Annotation���͡���������������ָ��Annotation��ElementType���ԡ�
@SuppressWarnings -- @SuppressWarnings ����ע���ݲ����ľ��棬�����������Щ���汣�־�Ĭ��
���� "@Deprecated �� @Override" ���ƣ�"@Documented, @Inherited, @Retention, @Target" ���ƣ����棬����ֻ�� @Deprecated, @Inherited, @SuppressWarnings �� 3 �� Annotation ����˵����

2.1) @Deprecated

@Deprecated �Ķ������£�

@Documented
@Retention(RetentionPolicy.RUNTIME)
public @interface Deprecated {
}
˵����

(01) @interface -- ������������ Deprecated����ζ�� Deprecated ʵ���� java.lang.annotation.Annotation �ӿڣ��� Deprecated ����һ��ע�⡣ (02) @Documented -- ����������˵����ע���ܳ����� javadoc �С�
(03) @Retention(RetentionPolicy.RUNTIME) -- ����������ָ�� Deprecated �Ĳ����� RetentionPolicy.RUNTIME�������ζ�ţ��������ὫDeprecated ����Ϣ������ .class �ļ��У������ܱ��������ȡ��
(04) @Deprecated ����ע���ݣ����ٱ�����ʹ�á�
���磬��ĳ�������� @Deprecated ��ע����÷������ٱ�����ʹ�á�����п�����Ա��ͼʹ�û���д�� @Deprecated ��ʾ�ķ����������������Ӧ����ʾ��Ϣ��ʾ������:



DeprecatedTest.java
import java.util.Date;
import java.util.Calendar;

public class DeprecatedTest {
    // @Deprecated ���� getString1(),��ʾ ���ǽ��鲻��ʹ�õĺ���
    @Deprecated
    private static void getString1(){
        System.out.println("Deprecated Method");
    }
    
    private static void getString2(){
        System.out.println("Normal Method");
    }
    
    // Date������/ʱ���ࡣjava�Ѿ�������ʹ�ø�����
    private static void testDate() {
        Date date = new Date(113, 8, 25);
        System.out.println(date.getYear());
    }
    // Calendar������/ʱ���ࡣjava����ʹ��Calendarȡ��Date��ʾ"����/ʱ��"
    private static void testCalendar() {
        Calendar cal = Calendar.getInstance();
        System.out.println(cal.get(Calendar.YEAR));
    }
    
    public static void main(String[] args) {
        getString1(); 
        getString2();
        testDate(); 
        testCalendar();
    }
}
˵����

������ eclipse �еĽ�ͼ���Ƚ����� "getString1() �� getString2()" �Լ� "testDate() �� testCalendar()" ��

(01) getString1() �� @Deprecated ��ע����ζ�Ž��鲻��ʹ�� getString1(); ���� getString1() �Ķ���͵���ʱ������һ���ߡ���һ������eclipse() �� @Deprecated �����Ĵ���

getString2() û�б� @Deprecated ��ע��������ʾ������

(02) testDate() ������ Date ����ط������� java �Ѿ����鲻��ʹ�� Date ��������/ʱ�䡣��ˣ��ڵ��� Date��API ʱ�������������Ϣ��;�е� warnings��

testCalendar() ������ Calendar �� API ����������/ʱ�䣬java ������ Calendar ȡ�� Date����ˣ����� Calendar ������� warning��

2.2) @Inherited

@Inherited �Ķ������£�

@Documented
@Retention(RetentionPolicy.RUNTIME)
@Target(ElementType.ANNOTATION_TYPE)
public @interface Inherited {
}
˵����

(01) @interface -- ������������ Inherited����ζ�� Inherited ʵ���� java.lang.annotation.Annotation �ӿڣ��� Inherited ����һ��ע�⡣
(02) @Documented -- ����������˵����ע���ܳ����� javadoc �С�
(03) @Retention(RetentionPolicy.RUNTIME) -- ����������ָ�� Inherited �Ĳ����� RetentionPolicy.RUNTIME�������ζ�ţ��������Ὣ Inherited ����Ϣ������ .class �ļ��У������ܱ��������ȡ��
(04) @Target(ElementType.ANNOTATION_TYPE) -- ����������ָ�� Inherited �������� ANNOTATION_TYPE�������ζ�ţ�@Inherited ֻ�ܱ�������ע "Annotation ����"��
(05) @Inherited �ĺ����ǣ�������ע��Annotation�����м̳��ԡ�
���裬���Ƕ�����ĳ�� Annotaion������������ MyAnnotation������ MyAnnotation ����עΪ @Inherited�����ڣ�ĳ���� Base ʹ����
MyAnnotation���� Base ������"������ע�� MyAnnotation"�����ڣ�Sub �̳��� Base������ MyAnnotation �� @Inherited��(���м̳���)�����ԣ�Sub Ҳ "������ע�� MyAnnotation"��

@Inherited ��ʹ��ʾ��:

InheritableSon.java
import java.lang.annotation.Target;
import java.lang.annotation.ElementType;
import java.lang.annotation.Retention;
import java.lang.annotation.RetentionPolicy;
import java.lang.annotation.Inherited;

/**
 * �Զ����Annotation��
 */
@Target(ElementType.TYPE)
@Retention(RetentionPolicy.RUNTIME)
@Inherited
@interface Inheritable
{
}

@Inheritable
class InheritableFather
{
    public InheritableFather() {
        // InheritableBase�Ƿ���� Inheritable Annotation
        System.out.println("InheritableFather:"+InheritableFather.class.isAnnotationPresent(Inheritable.class));
    }
}

/**
 * InheritableSon ��ֻ�Ǽ̳��� InheritableFather��
 */
public class InheritableSon extends InheritableFather
{
    public InheritableSon() {
        super();    // ���ø���Ĺ��캯��
        // InheritableSon���Ƿ���� Inheritable Annotation
        System.out.println("InheritableSon:"+InheritableSon.class.isAnnotationPresent(Inheritable.class));
    }
    
    public static void main(String[] args)
    {
        InheritableSon is = new InheritableSon();
    }
}
���н����

InheritableFather:true
InheritableSon:true
���ڣ����Ƕ� InheritableSon.java �����޸ģ�ע�͵� "Inheritable �� @Inherited ע��"��

InheritableSon.java
import java.lang.annotation.Target;
import java.lang.annotation.ElementType;
import java.lang.annotation.Retention;
import java.lang.annotation.RetentionPolicy;
import java.lang.annotation.Inherited;

/**
 * �Զ����Annotation��
 */
@Target(ElementType.TYPE)
@Retention(RetentionPolicy.RUNTIME)
//@Inherited
@interface Inheritable
{
}

@Inheritable
class InheritableFather
{
    public InheritableFather() {
        // InheritableBase�Ƿ���� Inheritable Annotation
        System.out.println("InheritableFather:"+InheritableFather.class.isAnnotationPresent(Inheritable.class));
    }
}

/**
 * InheritableSon ��ֻ�Ǽ̳��� InheritableFather��
 */
public class InheritableSon extends InheritableFather
{
    public InheritableSon() {
        super();    // ���ø���Ĺ��캯��
        // InheritableSon���Ƿ���� Inheritable Annotation
        System.out.println("InheritableSon:"+InheritableSon.class.isAnnotationPresent(Inheritable.class));
    }
    
    public static void main(String[] args)
    {
        InheritableSon is = new InheritableSon();
    }
}
���н����

InheritableFather:true
InheritableSon:false
�Ա������������������Ƿ��֣���ע�� Inheritable �� @Inherited ��עʱ�������м̳��ԡ�����û�м̳��ԡ�

2.3) @SuppressWarnings

@SuppressWarnings �Ķ������£�

@Target({TYPE, FIELD, METHOD, PARAMETER, CONSTRUCTOR, LOCAL_VARIABLE})
@Retention(RetentionPolicy.SOURCE)
public @interface SuppressWarnings {
    String[] value();
}
˵����

(01) @interface -- ������������ SuppressWarnings����ζ�� SuppressWarnings ʵ���� java.lang.annotation.Annotation �ӿڣ��� SuppressWarnings ����һ��ע�⡣

(02) @Retention(RetentionPolicy.SOURCE) -- ����������ָ�� SuppressWarnings �Ĳ����� RetentionPolicy.SOURCE�������ζ�ţ�SuppressWarnings ��Ϣ�������ڱ����������ڼ䣬������������֮�� SuppressWarnings ��û�������ˡ�

(03) @Target({TYPE, FIELD, METHOD, PARAMETER, CONSTRUCTOR, LOCAL_VARIABLE}) -- ����������ָ�� SuppressWarnings ������ͬʱ����TYPE, FIELD, METHOD, PARAMETER, CONSTRUCTOR, LOCAL_VARIABLE��

TYPE ��ζ�ţ����ܱ�ע"�ࡢ�ӿڣ�����ע�����ͣ���ö������"��
FIELD ��ζ�ţ����ܱ�ע"�ֶ�����"��
METHOD ��ζ�ţ����ܱ�ע"����"��
PARAMETER ��ζ�ţ����ܱ�ע"����"��
CONSTRUCTOR ��ζ�ţ����ܱ�ע"���췽��"��
LOCAL_VARIABLE ��ζ�ţ����ܱ�ע"�ֲ�����"��
(04) String[] value(); ��ζ�ţ�SuppressWarnings ��ָ������

(05) SuppressWarnings �������ǣ��ñ�������"������ע������"��ĳЩ���汣�־�Ĭ�����磬"@SuppressWarnings(value={"deprecation", "unchecked"})" ��ʾ��"������ע������"�е� "SuppressWarnings ���ٽ���ʹ�þ���"��"δ����ת��ʱ�ľ���"���ֳ�Ĭ��ʾ�����£�





SuppressWarningTest.java
import java.util.Date;

public class SuppressWarningTest {

    //@SuppressWarnings(value={"deprecation"})
    public static void doSomething(){
        Date date = new Date(113, 8, 26);
        System.out.println(date);
    }

    public static void main(String[] args) {
        doSomething();
    }
}
˵����

(01) ��ߵ�ͼ�У�û��ʹ�� @SuppressWarnings(value={"deprecation"}) , �� Date ���� java ���ٽ���ʹ�õ��ࡣ��ˣ����� Date �� API ʱ����������档���ұߵ�;�У�ʹ���� @SuppressWarnings(value={"deprecation"})����ˣ���������"���� Date �� API �����ľ���"���ֳ�Ĭ��

���䣺SuppressWarnings ���õĹؼ��ֵı��

deprecation  -- ʹ���˲��޳�ʹ�õ���򷽷�ʱ�ľ���
unchecked    -- ִ����δ����ת��ʱ�ľ��棬���統ʹ�ü���ʱû���÷��� (Generics) ��ָ�����ϱ�������͡�
fallthrough  -- �� Switch �����ֱ��ͨ����һ�������û�� Break ʱ�ľ��档
path         -- ����·����Դ�ļ�·�������в����ڵ�·��ʱ�ľ��档
serial       -- ���ڿ����л�������ȱ�� serialVersionUID ����ʱ�ľ��档
finally      -- �κ� finally �Ӿ䲻���������ʱ�ľ��档
all          -- ����������������ľ��档
# 4��Annotation ������
Annotation ��һ�������࣬���� Junit��Struts��Spring �ȹ��߿���б��㷺ʹ�á�

�����ڱ���о�����ʹ�õ��� Annotation �����У�

# 1��������
Annotation ����"�ñ��������б����������"��

���磬@SuppressWarnings, @Deprecated �� @Override �����б��������á�

(01) ���� @SuppressWarnings �� @Deprecated���Ѿ���"��3����"����ϸ���ܹ��ˡ�����Ͳ��پ���˵���ˡ�

(02) ��ĳ�������� @Override �ı�ע������ζ�Ÿ÷����Ḳ�Ǹ����е�ͬ������������з����� @Override ��ʾ����������ȴû��"�� @Override ��ע"��ͬ����������������ᱨ��ʾ�����£�



OverrideTest.java
public class OverrideTest {

    /**
     * toString() ��java.lang.Object�ж��壻
     * ��ˣ������� @Override ��ע�ǶԵġ�
     */
    @Override
    public String toString(){
        return "Override toString";
    }

    /**
     * getString() û����OverrideTest���κθ����ж��壻
     * ���ǣ�����ȴ�� @Override ��ע����˻�����������
     */
    @Override
    public String getString(){
        return "get toString";
    }
    
    public static void main(String[] args) {
    }
}
�����Ǹó����� eclipse �еĽ�ͼ�����У����ǿ��Է��� "getString()" �����ᱨ��������Ϊ "getString() �� @Override ����ע������OverrideTest ���κθ����ж�û�ж��� getString1() ����"��

"�� getString() ����� @Overrideע�͵�"�����ɽ���ô���

# 2) �ڷ�����ʹ�� Annotation
�ڷ���� Class, Method, Field �Ⱥ����У�������� Annotation ��صĽӿڡ�

��Ҳ��ζ�ţ����ǿ����ڷ����н�����ʹ�� Annotation��

AnnotationTest.java
import java.lang.annotation.Annotation;
import java.lang.annotation.Target;
import java.lang.annotation.ElementType;
import java.lang.annotation.Retention;
import java.lang.annotation.RetentionPolicy;
import java.lang.annotation.Inherited;
import java.lang.reflect.Method;

/**
 * Annotation�ڷ��亯���е�ʹ��ʾ��
 */
@Retention(RetentionPolicy.RUNTIME)
@interface MyAnnotation {
    String[] value() default "unknown";
}

/**
 * Person�ࡣ����ʹ��MyAnnotationע�⡣
 */
class Person {
    
    /**
     * empty()����ͬʱ�� "@Deprecated" �� "@MyAnnotation(value={"a","b"})"����ע 
     * (01) @Deprecated����ζ��empty()���������ٱ�����ʹ��
     * (02) @MyAnnotation, ��ζ��empty() ������Ӧ��MyAnnotation��valueֵ��Ĭ��ֵ"unknown"
     */
    @MyAnnotation
    @Deprecated
    public void empty(){
        System.out.println("\nempty");
    }
    
    /**
     * sombody() �� @MyAnnotation(value={"girl","boy"}) ����ע��
     * @MyAnnotation(value={"girl","boy"}), ��ζ��MyAnnotation��valueֵ��{"girl","boy"}
     */
    @MyAnnotation(value={"girl","boy"})
    public void somebody(String name, int age){
        System.out.println("\nsomebody: "+name+", "+age);
    }
}

public class AnnotationTest {

    public static void main(String[] args) throws Exception {
        
        // �½�Person
        Person person = new Person();
        // ��ȡPerson��Classʵ��
        Class<Person> c = Person.class;
        // ��ȡ somebody() ������Methodʵ��
        Method mSomebody = c.getMethod("somebody", new Class[]{String.class, int.class});
        // ִ�и÷���
        mSomebody.invoke(person, new Object[]{"lily", 18});
        iteratorAnnotations(mSomebody);
        

        // ��ȡ somebody() ������Methodʵ��
        Method mEmpty = c.getMethod("empty", new Class[]{});
        // ִ�и÷���
        mEmpty.invoke(person, new Object[]{});        
        iteratorAnnotations(mEmpty);
    }
    
    public static void iteratorAnnotations(Method method) {

        // �ж� somebody() �����Ƿ����MyAnnotationע��
        if(method.isAnnotationPresent(MyAnnotation.class)){
            // ��ȡ�÷�����MyAnnotationע��ʵ��
            MyAnnotation myAnnotation = method.getAnnotation(MyAnnotation.class);
            // ��ȡ myAnnotation��ֵ������ӡ����
            String[] values = myAnnotation.value();
            for (String str:values)
                System.out.printf(str+", ");
            System.out.println();
        }
        
        // ��ȡ�����ϵ�����ע�⣬����ӡ����
        Annotation[] annotations = method.getAnnotations();
        for(Annotation annotation : annotations){
            System.out.println(annotation);
        }
    }
}
���н����

somebody: lily, 18
girl, boy, 
@com.skywang.annotation.MyAnnotation(value=[girl, boy])

empty
unknown, 
@com.skywang.annotation.MyAnnotation(value=[unknown])
@java.lang.Deprecated()
3) ���� Annotation ���ɰ����ĵ�
ͨ���� Annotation ע����� @Documented ��ǩ����ʹ�� Annotation ��ǩ������ javadoc �С�

4) �ܹ���æ�鿴�鿴����
ͨ�� @Override, @Deprecated �ȣ������ܷܺ�����˽����Ĵ��½ṹ��

���⣬����Ҳ����ͨ���Զ��� Annotation ��ʵ��һЩ���ܡ�

ԭ�ĵ�ַ��https://www.cnblogs.com/skywang12345/p/3344137.html
