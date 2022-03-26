 A=[10 -7 0 1;-3 2.09999999999999 6 2;5 -1 5 -1;0 1 0 2];
b=[8;5.90000000000001;5 ;1];
n=length(A);
U=zeros(n);L=eye(n,n);
for i=1:n
row=i;
for col=row:n
sum=0;
for k=1:row-1
sum=sum+L(row,k)*U(k,col);
end
U(row,col)=A(row,col)-sum;
end
col=i;
for  row=col+1:n
sum=0;
for  k=1:col-1
sum=sum+L(row,k)*U(k,col);
end
L(row,col)=(A(row,col)-sum)/U(col,col);
end
end
y=zeros(n,1);

y(1)=b(1);
for  i=2:n
y(i)=b(i)-L(i,1:i-1)*y(1:i-1);
end
x=zeros(n,1);
x(n)=y(n)/U(n,n)

for i=1:n-1;
k=n-i;
x(k)=(y(k)-U(k,k+1:n)*x((k+1:n))/U(k,k);end